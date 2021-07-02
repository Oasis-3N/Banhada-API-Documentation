Account api
======================

/account/register (POST)
-----------------------------------------------

    **새로운 사용자가 회원가입을 시도**

    :Paramaters:

        **email**

        - name: email
        - in: json
        - description: 새로운 사용자의 이메일
        - required: true

        **id**

        - name: id
        - in: json
        - description: 새로운 사용자의 아이디
        - required: true

        **username**

        - name: username
        - in: json
        - description: 새로운 사용자의 이름
        - required: true

        **password**

        - name: password
        - in: json
        - description: 새로운 사용자의 비밀번호
        - required: true

        **address**

        - name: address
        - in: json
        - description: 새로운 사용자의 주소
        - required: true

        **nickname**

        - name: nickname
        - in: json
        - description: 새로운 사용자의 닉네임
        - required: true

    **Example request**

    .. sourcecode:: http

        POST /account/register HTTP/1.1
        Host: 52.79.54.196:2500
        Content-Type: application/json

            {
                "email": "brankein13@gm.gist.ac.kr",
                "id": "BranKein13",
                "username": "김연혁",
                "password": "password",
                "address": "광주광역시 북구 첨단과기로 123 (오룡동)",
                "nickname": "프노"
            }

    **Example response**

    .. sourcecode:: http

        HTTP/1.1 200 OK


    :resheader Content-Type: application/json
    :status:
        - 200: 성공적으로 요청을 수행함
        - 400: 파라미터의 길이가 너무 김
        - 500: 알수 없는 오류 발생

/account/login (POST)
------------------------------------------------------

    **로그인**

    :Paramaters:

        **id**

        - name: id
        - in: json
        - description: 사용자의 아이디
        - required: true

        **password**

        - name: password
        - in: json
        - description: 사용자의 패스워드
        - required: true


    **Example request**

    .. sourcecode:: http

        GET /account/login HTTP/1.1
        Host: 52.79.54.196:2500

    **Example response**

    .. sourcecode:: http

        HTTP/1.1 200 OK

    :resheader Content-Type: application/json
    :status:
        - 200: 성공적으로 요청을 수행함
        - 403: 로그인 실패

/account/user_data (GET)
--------------------------------------------------

    **사용자의 정보 가져오기**

    :Paramaters:

        **id**

        - name: id
        - in: query_string
        - description: 가져올 사용자의 아이디
        - required: true

    **Example request**

    .. sourcecode:: http

        GET /account/user_data HTTP/1.1
        Host: 52.79.54.196:2500
        Response-Type: application/json

    **Example response**

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-Type: application/json

            {
                "address": "광주광역시 북구 첨단과기로 123 (오룡동)",
                "email": "brankein13@gm.gist.ac.kr",
                "id": "BranKein13",
                "nickname": "프노",
                "username": "김연혁",
                "uuid": "e453b76a-5c7d-43a4-8d7c-c802435faf4d"
            }

    :resheader Content-Type: application/json
    :status:
        - 200: 성공적으로 요청을 수행함
        - 500: 알 수 없는 오류 발생
