# OpenAPIProject
# { 청약 API } 안드로이드 개인 과제
주택 관리 번호, 공고 번호, 공고 지역 코드, 모집 공고일 값 -> 분양 정보의 상세 정보 제공
property_openapiproject_231103_assignment


* 주요 파일
  * CyListAdapter.kt
  * RetrofitClient.kt
  * CyApiService.kt - 인터페이스

  
# RetrofitClient.kt

    open fun getInstance() : Retrofit {
        if (instance == null) {
            instance = Retrofit.Builder()
                .baseUrl(BASE_URL)
                .addConverterFactory(GsonConverterFactory.create())
                .build()

        } // end if

        return instance!!
    }





# CyApiService.kt
    
    @GET("ApplyhomeInfoDetailSvc/v1/getAPTLttotPblancDetail")
    fun getAPTLttotPblancDetail(
        @Query("page")
        page: Int = 1,
        @Query("perPage")
        perPage: Int = 10,
        @Query("serviceKey")
        serviceKey: String = authKey
    ) : Call<AptLttotPblancDetailDTO>

