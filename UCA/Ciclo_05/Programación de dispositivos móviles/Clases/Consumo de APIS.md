---
tags:
  - "#PDM"
---
## Arquitectura
Distribución (Arquitectura de cebolla): Consiste en separar en tres capas la app.

Proyect
	>Data
		>di (inyección de dependencia)
			Se configura el consumo de las APIS
		>model
			Entidad de bases de datos
		>remote
			Conexión a la API más específico
		>repository
	>Domain
	>UI
		>Converter
		>List
		>Navigation
		>Theme
	Main Activity

## Manifest

``` kotlin
<application
	android:name=".AppName"
>

// En una clase distinta (en cualquier lado)
@HiltAndroidApp
class AppName : Aplication()
```

# Ejemplo de consumo de una API de valor de monedas

``` kotlin
//Una kotlin file en model, permite recibir la respuesta de la API

data class CurrencyRate{
	val base: String,
	val rates: Map<String, Double> //Es un Map pq la API devuelve un diccionario
}
```


``` kotlin
// kotlin file en remote

import retrofit2.http.GET

interface CurrencyApiService {
	
	@GET("lastest.json")
	suspend fun getLatestRates(): CurrencyRate 
	
}
```

``` kotlin
//kotlin file en repository

class CurrencyRepository @Inject constructor(
	private val apiService: CurrencyApiService
) {
	suspend fun getCurrencyRates(): CurrencyRate {
		return apiService.getLatestRates()
	}
}
```

``` kotlin
//kotlin file en domain

class GetCurrencyRatesUseCase @Inject constructor(
	private val repository: CurrencyRepository
){
	suspend operator fun invoke(): CurrencyRate{
		return repository.getCurrencyRates()
	}
}
```

``` kotlin
//kotlin file en di

@Module
@InstallIn(SingletonComponent::class)
object NetworkModule{
	@Provides
	@Singleton
	fun provideLoginInterceptor(): HttpLoginInterceptor{
			return HttpLoginInterceptor().apply {
			level = HttpLoginInterceptor.Level.BODY
		}
	}
	
	@Provides
	@Singleton
	fun provideHttpClient(LoginInterceptor: HttpLoginInterceptor): OkHttpClient{
		return OkHttpClient.Builder().addInterceptor(loginInterceptor).build()
	} 
	
	@Provides
	@Singleton
	fun provideRetrofit(okHttpClient: OkHttpClient): Retrofit {
		return Retrofit.Builder()
			.baseUrl("ApiLink") /*Se pone lo que se piensa que siempre se
								utilizará, es decir la url base de la API*/
			.addConverterFactory(GsonConverterFactory.create())
			.client(okHttpClient)
			.build()
	}

	@Provide
	@Singleton
	fun provideCurrencyApiService(retrofit: Retrofit): CurrencyApiService {
			return retrofit.create(CurrencyApiService::class.java)
	}
}
```

``` kotlin
//kotlin file en List

data class CurrencyListUiState(
	val loading: Boolean = false,
	val error: String? = null,
	val rates: Map<String, Double> = emptyMap()
)
```

``` kotlin
//kotlin file en 

@HiltViewModel
class CurrencyListViewModel @Inject constructor(
	private val getCurrencyRatesUseCase : GetCurrencyRateUseCase
): ViewModel() {
	private val _uiState = MutableStateFlow(CurrencyListUiState())
	val uiState: StateFlow<CurrencyListUiState> = _uiState
	
	init {
		fetchCurrencyRates()
	}
	
	private fun fetchCurrencyRates(){
		viewModelScope.launch {
			_uiState.update{ it.copy(loading = true, error = null) }
		try {
			val currencyRate = getCurrencyRatesUseCase()
			
			_uiState.update { it.copy(loading = false ,
				rates = currencyRate.rates 
			) }
			
		} catch (e: Exception) {
			_uiState.update { it.copy(loading = false, error = e.localizeMessage)}
		}	
	}
}
```

``` kotlin
//kotlin file en List

@Composable
fun CurrencyLustScreen(
	viewModel: CurrencyListViewModel = hiltViewModel(),
	onNavigateToConverter: (String) -> Unit
){
	val uiState by viewMOdel.uiState.collectAsState()

	Column {
		Text("Lista de monedas")
		if(uiState.loading){
			Column{
				CircularProgressIndicator()
			}
		} else if(uiState.error != null) {
			Text("Ha ocurrido un error")
		} else {
			// La pantalla en general
			
			LazyColumn {
				items(uiState.rates.keys.toList()){ currencyCode ->
					Text(currencyCode)
				}
			}
		}
	}
}
```



