Article api
======================

/article/get_articles (GET)
-----------------------------------------------

    **특정 주소지에 올라와있는 게시물을 조회**

    :Paramaters:

        **address**

        - name: address
        - in: query_string
        - description: 주소지
        - required: true

        **id**

        - name: id
        - in: query_string
        - description: 조회하는 사용자의 아이디
        - required: true

        **article_type**

        - name: article_type
        - in: query_string
        - description: 신선 or 배달 중 선택
        - required: false

        **article_category**

        - name: article_category
        - in: query_string
        - description: 게시물의 카테고리 중 하나를 선택
        - required: false

        **start_idx**

        - name: start_idx
        - in: query_string
        - description:
        - required: false

        **end_idx**

        - name: end_idx
        - in: query_string
        - description:
        - required: false

    **Example request**

    .. sourcecode:: http

        GET /article/get_articles?address=광주광역시 북구 첨단과기로 123 (오룡동)&id=BranKein13 HTTP/1.1
        Host: 52.79.54.196:2500

    **Example response**

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-Type: application/json

            [
                {
                    "cost": 10000,
                    "fork": "unactive",
                    "id": 1,
                    "image": "no image",
                    "is_visible": 1,
                    "reg_date": "Mon, 04 Jan 2021 00:58:29 GMT",
                    "submitter": "프노",
                    "title": "첫 테스트"
                },
                {
                    "cost": 20000,
                    "fork": "unactive",
                    "id": 2,
                    "image": "no image",
                    "is_visible": 1,
                    "reg_date": "Mon, 04 Jan 2021 04:01:46 GMT",
                    "submitter": "연어",
                    "title": "게시물1"
                }
            ]

    :resheader Content-Type: application/json
    :status:
        - 200: 성공적으로 요청을 수행함
        - 500: 알수 없는 오류 발생

/article/get_article/<int:article_id> (GET)
------------------------------------------------------

    **게시물의 상세 정보를 가져옴**

    :Paramaters:

        **article_id**

        - name: article_id
        - in: query
        - description: 가져오려는 게시물의 아이디
        - required: true

    **Example request**

    .. sourcecode:: http

        GET /article/get_article/1 HTTP/1.1
        Host: 52.79.54.196:2500

    **Example response**

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-Type: application/json

            {
                "address": "광주광역시 북구 첨단과기로 123 (오룡동)",
                "article_category": "유제품",
                "article_type": "신선",
                "content": "난 연어가 아니다",
                "cost": 10000,
                "id": 1,
                "image": "no image",
                "is_visible": 1,
                "max_num": 1,
                "reg_date": "Mon, 04 Jan 2021 00:58:29 GMT",
                "remain_time": 20,
                "submitter": "프노",
                "submitter_image": "no image",
                "submitter_result": 50,
                "title": "첫 테스트",
                "views": 0
            }

    :resheader Content-Type: application/json
    :status:
        - 200: 성공적으로 요청을 수행함
        - 404: 게시물이 존재하지 않음

/article/create_article (POST)
--------------------------------------------------

    **게시물 작성**

    :Paramaters:

        **title**

        - name: title
        - in: json
        - description: 제목
        - required: true

        **submitter**

        - name: submitter
        - in: json
        - description: 사용자의 아이디
        - required: true

        **address**

        - name: address
        - in: json
        - description: 주소지
        - required: true

        **cost**

        - name: cost
        - in: json
        - description: 가격
        - required: true

        **remain_time**

        - name: remain_time
        - in: json
        - description: 게시물이 공개되는 시간
        - required: true

        **max_num**

        - name: max_num
        - in: json
        - description: 모으는 최대 명수
        - required: true

        **article_type**

        - name: article_type
        - in: json
        - description: 신선 or 배달 중 선택
        - required: true

        **article_category**

        - name: article_category
        - in: json
        - description: 카테고리 중 하나 선택
        - required: true

        **image**

        - name: image
        - in: json
        - description: 이미지
        - required: false

        **content**

        - name: content
        - in: json
        - description: 설명
        - required: false

    **Example request**

    .. sourcecode:: http

        GET /account/user_data HTTP/1.1
        Host: 52.79.54.196:2500
        Content-Type: application/json

            {
                "title": "게시물1",
                "submitter": "6712kyh",
                "address": "광주광역시 북구 첨단과기로 123 (오룡동)",
                "cost": "20000",
                "remain_time": "20",
                "max_num": "1",
                "article_type": "신선",
                "article_category": "유제품",
                "content": "난 연어다"
            }

    **Example response**

    .. sourcecode:: http

        HTTP/1.1 200 OK

    :resheader Content-Type: application/json
    :status:
        - 200: 성공적으로 요청을 수행함
        - 500: 알 수 없는 오류 발생
