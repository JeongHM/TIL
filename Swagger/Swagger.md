Swagger에대해 기술합니다 

## Swagger ?

---

웹 서비스에서 API 서버가 어떤 스펙을 가지고 있으는지에 대한 문서를 작업할 수 있도록 도와주는 프레임 워크 

- YAML, JSON 형식으로 작성 → 서버에 접속 시 문서 페이지를 확인 하는 기능 제공
- 데이터 입력, 버튼 클릭으로 실제 통신을 보내고 응답 받을 수 있음

## Swagger Format (YAML)

---
```YAML
    swagger: '2.0'                         # Swagger Version
    info: 
    	description: Test API V1             # API 문서 설명
      version: "1.0.0"                     # API 버전 
      title: Test Title                    # API 타이틀
      contact:
        email: your_email@email.com        # contact point
    
    tags:                                  # API Route Tags (BluePrint 와 같이 사용)
    - name: api/v1                         # Tags의 라우터 정보?
      description: This is Test API
    
    paths:                                 # 컨트롤러에 해당 되는 부분
    	/index:                              # Route
    	    get:                             # Method
    	      tags:                          # Tag가 있다면 사용 아니면 pass
    	        - api/v1
    	      summary: get Index Page        # 해당 API의 설명
    	      security:                      # Auth 설정 부분
    	        - ApiKeyAuth: []
    	      responses:                     # Response
    	        200:
    	          description: 'Success'
    	          schema:
    	            $ref: '#/definitions/200' # Model 에서 정의되어있는 부분을 가져오는 부분
    
    definitions:                            # Model로 정하는 곳
      200:
        type: object
        properties:
          code:
            type: integer
            format: int3
            example: 200
          status:
            type: string
            example: 'success'
          message:
            type: string
            example: 'success'
```
