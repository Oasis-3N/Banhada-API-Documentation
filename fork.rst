Fork api
======================

/fork/make_fork (POST)
-----------------------------------------------

    **특정 게시물을 포크**

    :Paramaters:

        **id**

        - name: id
        - in: json
        - description: 포크하는 사용자의 아이디
        - required: true

        **article_id**

        - name: article_id
        - in: json
        - description: 포크하는 게시물의 아이디
        - required: true


    **Example request**

    .. sourcecode:: http

        POST /fork/make_fork HTTP/1.1
        Host: 52.79.54.196:2500
        Content-Type: application/json

            {
                "id": "Brankein13",
                "article_id": "1"
            }

    **Example response**

    .. sourcecode:: http

        HTTP/1.1 200 OK

    :resheader Content-Type: application/json
    :status:
        - 200: 성공적으로 요청을 수행함
        - 500: 알 수 없는 오류 발생

/fork/delete_fork (DELETE)
------------------------------------------------------

    **포크를 삭제**

    :Paramaters:

        **id**

        - name: id
        - in: json
        - description: 포크를 삭제하는 사용자의 아이디
        - required: true

        **article_id**

        - name: article_id
        - in: jaon
        - description: 포크를 삭제하는 게시물의 아이디
        - required: true


    **Example request**

    .. sourcecode:: http

        GET /message/get_message_groups?id=BranKein13 HTTP/1.1
        Host: 52.79.54.196:2500
        Content-Type: application/json

            {
                "id": "BranKein13",
                "article_id": 1
            }

    **Example response**

    .. sourcecode:: http

        HTTP/1.1 200 OK

    :resheader Content-Type: application/json
    :status:
        - 200: 성공적으로 요청을 수행함

/fork/get_fork_list (GET)
--------------------------------------------------

    **포크한 게시물들만 가져옴**

    :Paramaters:

        **id**

        - name: id
        - in: query_string
        - description: 포크한 게시물들을 가져올 사용자의 아이디
        - required: true


    **Example request**

    .. sourcecode:: http

        GET /fork/get_fork_list HTTP/1.1
        Host: 52.79.54.196:2500
        Response-Type: application/json

    **Example response**

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-Type: application/json

            [
                {
                    "cost": 10000,
                    "fork_num": 1,
                    "id": 1,
                    "image": "",
                    "remain_time": 20,
                    "submitter": "프노",
                    "title": "첫 테스트",
                    "views": 1
                }
            ]

    :resheader Content-Type: application/json
    :status:
        - 200: 성공적으로 요청을 수행함

