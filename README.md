{ 청약 API } 안드로이드 개인 과제

# OpenAPIProject
property_openapiproject_231103_assignment


# 주요 파일
# RetrofitClient.kt
package com.example.openapiproject.network

import com.google.gson.GsonBuilder
import retrofit2.Retrofit
import retrofit2.converter.gson.GsonConverterFactory

object RetrofitClient {
    /* Open API End Point Url */
    private const val BASE_URL = "https://api.odcloud.kr/api/"
    private var instance: Retrofit? = null

    open fun getInstance() : Retrofit {
        if (instance == null) {
            instance = Retrofit.Builder()
                .baseUrl(BASE_URL)
                .addConverterFactory(GsonConverterFactory.create())
                .build()

        } // end if

        return instance!!
    }

}



# CyApiService.kt
package com.example.openapiproject.network

import com.example.openapiproject.network.responseDTO.AptLttotPblancDetailDTO
import retrofit2.Call
import retrofit2.http.GET
import retrofit2.http.Query

/**
 * 청약 API
 */
interface CyApiService {

    companion object {
        // 발급받은 서비스 키
        private const val authKey = "2XdTyQg8UpkQZbYwCAI7QOktDUUaH0WRVKLRUQ1rpxkddWw1H2tsG5W1Sg1SzQvygpSUw8pYMtzZgwZkpdKrlQ=="

    }

    // 주택 관리 번호, 공고 번호, 공고 지역 코드, 모집 공고일 값을 이용하여 APT 분양 정보의 상세 정보를 제공
    @GET("ApplyhomeInfoDetailSvc/v1/getAPTLttotPblancDetail")
    fun getAPTLttotPblancDetail(
        @Query("page")
        page: Int = 1,
        @Query("perPage")
        perPage: Int = 10,
        @Query("serviceKey")
        serviceKey: String = authKey
    ) : Call<AptLttotPblancDetailDTO>

}  
