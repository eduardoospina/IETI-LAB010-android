# IETI-LAB010-android

## AUTOR.

Eduardo Ospina Mejia


## Proyecto Integrador: configuración servicios para consumir API REST con Retrofit

1) Agrega la dependencia de Retrofit en los archivos del build.gradle:

![](https://i.postimg.cc/mD9LwZ98/andapi-1.png)

![](https://i.postimg.cc/tJt9Kr26/andapi-2.png)


2) //Retrofit

![](https://i.postimg.cc/5NgxpRHd/andapi-3.png)


3) implementation "com.squareup.retrofit2:retrofit:2.9.0"

![](https://i.postimg.cc/8zCTYmWF/andapi-4.png)


4) implementation 'com.squareup.okhttp3:logging-interceptor:4.9.0'

![](https://i.postimg.cc/13Yy1Vcv/andapi-5.png)


5) implementation 'com.squareup.okhttp3:logging-interceptor:5.0.0-alpha.2'

![](https://i.postimg.cc/437sf4Ws/andapi-6.png)


6) implementation 'com.squareup.retrofit2:converter-gson:2.9.0'

![](https://i.postimg.cc/rm5T4n6H/andapi-7.png)

![](https://i.postimg.cc/L5Rp3t28/andapi-8.png)

![](https://i.postimg.cc/hvrqyXtb/andapi-9.png)


7) Implementa los Dtos de los servicios que vas a consumir (AuthController y TaskController)

![](https://i.postimg.cc/CMHYLQsB/andapi-10.png)


8) Implementa las interfaces de los servicios que vas a consumir con los metodos HTTP requeridos ( Utiliza como base la documentación oficial de Retrofit, también basate en tu FrontEnd para saber cuales son los metodos que necesitas para construir la UI )


9) Implementa la interfaz del Storage con las funciones para almacenar tu Token.

![](https://i.postimg.cc/QCBpSTbv/andapi-10-5.png)


10) Implementa el AuthInterceptor utilizando el Storage para agregar tu Token de sesión en el Authorization header. ( Utiliza este blog para saber como añadir el header a tu Interceptor )

![](https://i.postimg.cc/VvMFmtCn/andapi-10-6.png)


11) Crea una instancia de Retrofit:

	`Gson gson = new GsonBuilder().setDateFormat( "yyyy-MM-dd'T'HH:mm:ss" ).create();

	Retrofit.Builder builder = new Retrofit.Builder().baseUrl( BuildConfig.API_BASE_URL ).addConverterFactory( GsonConverterFactory.create( gson ) ).addCallAdapterFactory( RxJavaCallAdapterFactory.createWithScheduler( Schedulers.io() ) );

	HttpLoggingInterceptor loggingInterceptor = new HttpLoggingInterceptor(); loggingInterceptor.setLevel( HttpLoggingInterceptor.Level.BODY );

	OkHttpClient okHttpClient = new OkHttpClient.Builder().addInterceptor( loggingInterceptor ) .addInterceptor(new AuthInterceptor(storage)) .writeTimeout( 0, TimeUnit.MILLISECONDS ).readTimeout( 2, TimeUnit.MINUTES ).connectTimeout( 1, TimeUnit.MINUTES ).build(); return builder.client( okHttpClient ).build();`

![](https://i.postimg.cc/Wb5v0qKs/andapi-11.png)

12) Prueba tu endpoint call llamandolo en el metodo onCreate de tu actividad principal para saber si los datos estan cargando

