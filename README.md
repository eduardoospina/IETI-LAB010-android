# IETI-LAB010-android

## AUTOR.

Eduardo Ospina Mejia


## Proyecto Integrador: configuración servicios para consumir API REST con Retrofit

1) Agrega la dependencia de Retrofit en los archivos del build.gradle:


2) //Retrofit


3) implementation "com.squareup.retrofit2:retrofit:2.9.0"


4) implementation 'com.squareup.okhttp3:logging-interceptor:4.9.0'


5) implementation 'com.squareup.okhttp3:logging-interceptor:5.0.0-alpha.2'


6) implementation 'com.squareup.retrofit2:converter-gson:2.9.0'


7) Implementa los Dtos de los servicios que vas a consumir (AuthController y TaskController)


8) Implementa las interfaces de los servicios que vas a consumir con los metodos HTTP requeridos ( Utiliza como base la documentación oficial de Retrofit, también basate en tu FrontEnd para saber cuales son los metodos que necesitas para construir la UI )


9) Implementa la interfaz del Storage con las funciones para almacenar tu Token.


10) Implementa el AuthInterceptor utilizando el Storage para agregar tu Token de sesión en el Authorization header. ( Utiliza este blog para saber como añadir el header a tu Interceptor )


11) Crea una instancia de Retrofit:

	`Gson gson = new GsonBuilder().setDateFormat( "yyyy-MM-dd'T'HH:mm:ss" ).create();

	Retrofit.Builder builder = new Retrofit.Builder().baseUrl( BuildConfig.API_BASE_URL ).addConverterFactory( GsonConverterFactory.create( gson ) ).addCallAdapterFactory( RxJavaCallAdapterFactory.createWithScheduler( Schedulers.io() ) );

	HttpLoggingInterceptor loggingInterceptor = new HttpLoggingInterceptor(); loggingInterceptor.setLevel( HttpLoggingInterceptor.Level.BODY );

	OkHttpClient okHttpClient = new OkHttpClient.Builder().addInterceptor( loggingInterceptor ) .addInterceptor(new AuthInterceptor(storage)) .writeTimeout( 0, TimeUnit.MILLISECONDS ).readTimeout( 2, TimeUnit.MINUTES ).connectTimeout( 1, TimeUnit.MINUTES ).build(); return builder.client( okHttpClient ).build();`

12) Prueba tu endpoint call llamandolo en el metodo onCreate de tu actividad principal para saber si los datos estan cargando

