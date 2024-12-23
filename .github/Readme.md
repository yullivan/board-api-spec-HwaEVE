# 1. 게시판 생성 Request (POST 요청)
## URL: /api/board
### Method: POST

Body:
>제목(title)
>작성자(userId)

Response:
># Status Code: 201 Created
>Body: 게시글의 ID와 생성된 데이터를 반환
> * 제목(title) [STring]
> * 작성자(userId) [String]
* Json

>{
> 
>"title": "새로운 게시글 제목",
> 
>"content": "게시글 내용입니다.",
> 
>"userId": 1
}

# 2. 게시판 조회 (Get Post) Request (GET 요청)
## URL: /api/board/{id}
### Method: GET

Path Parameter:
>id: 게시글 ID

Response
> * Status Code: 200 OK
> * Body: 게시글의 상세 정보 반환

# 3. 게시판 목록 조회 (List Posts) Request (GET 요청)
## URL: /api/board
### Method: GET
   
Query Parameters:
> * page: 페이지 번호 (기본값 0)
> * size: 페이지 크기 (기본값 10)
> * sort: 정렬 기준 (옵션, 예: title,desc)

Response
> * Status Code: 200 OK
> * Body: 게시글 목록 (페이징 처리 포함)


# 4. 게시판 글 수정 (Update Post) Request (PUT 요청)
## URL: /api/board/{id}
### Method: PUT

Path Parameter:
>id: 게시글 ID

Body:
> * 제목(title) [String]

# 5. 게시판 삭제 (Delete Board)
## Method: DELETE
### URL: /api/board/{id}

Path Parameter:
> id: 삭제할 게시판 ID

Response
> Status Code: 204 No Content
> * 응답 본문은 없으며, 게시판이 성공적으로 삭제되었음을 나타냅니다.

---------------------------------------------------------------------
# 1.게시글 생성 (Create Post)
## Method: POST
### URL: /api/board/{boardId}/post

Path Parameter:
>boardId: 게시글을 작성할 게시판 ID

Body:
> * title (String): 게시글 제목
> * content (String): 게시글 내용
> * userId (String): 작성자 ID

json

>{
>"title": "새로운 게시글 제목"
> 
>"content": "게시글 내용입니다.",
> 
>"userId": 1
}

Response
>* Status Code: 201 Created
>* Body: 생성된 게시글의 ID 및 정보

# 2. 게시글 조회 (Get Post)
## Method: GET
### URL: /api/board/{boardId}/post/{postId}

Path Parameter:
> * boardId: 게시글이 속한 게시판 ID
> * postId: 게시글 ID

Response
>Status Code: 200 OK
> 
>Body: 요청된 게시글의 상세 정보

# 3.게시글 목록 조회 (List Posts)
## Method: GET
### URL: /api/board/{boardId}/posts

Path Parameter:
>boardId: 게시글 목록을 조회할 게시판 ID

Query Parameters:
>* page: 페이지 번호 (기본값 0)
>* size: 페이지 크기 (기본값 10)
>* sort: 정렬 기준 (예: createdAt,desc)

Response
>* Status Code: 200 OK
>* Body: 게시글 목록 및 페이징 정보

# 4. 게시글 수정 (Update Post)
## Method: PUT
### URL: /api/board/{boardId}/post/{postId}

Path Parameter:
>* boardId: 게시글이 속한 게시판 ID
>* postId: 수정할 게시글 ID

Body:
>* title (String): 수정된 게시글 제목
>* content (String, Optional