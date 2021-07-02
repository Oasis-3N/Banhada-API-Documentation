Message api
======================

/message/get_messages (GET)
-----------------------------------------------

    **특정 채팅방의 채팅 목록을 가져옴**

    :Paramaters:

        **group_id**

        - name: group_id
        - in: query_string
        - description: 가져올 채팅의 채팅방 id
        - required: true


    **Example request**

    .. sourcecode:: http

        GET /message/get_messages?group_id=1 HTTP/1.1
        Host: 52.79.54.196:2500

    **Example response**

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-Type: application/json

            [
                {
                    "image": "",
                    "message": "",
                    "profile_image": null,
                    "reg_date": "Mon, 04 Jan 2021 03:54:16 GMT",
                    "submitter": "프노"
                },
                {
                    "image": "",
                    "message": "안녕",
                    "profile_image": null,
                    "reg_date": "Mon, 04 Jan 2021 03:54:39 GMT",
                    "submitter": "프노"
                },
                {
                    "image": "",
                    "message": "나도 안녕",
                    "profile_image": null,
                    "reg_date": "Mon, 04 Jan 2021 03:55:21 GMT",
                    "submitter": "연어"
                }
            ]

    :resheader Content-Type: application/json
    :status:
        - 200: 성공적으로 요청을 수행함
        - 404: 해당 그룹이 존재하지 않음

/message/get_message_groups (GET)
------------------------------------------------------

    **특정 사용자의 모든 채팅방 목록을 가져옴**

    :Paramaters:

        **id**

        - name: id
        - in: query_string
        - description: 사용자의 아이디
        - required: true


    **Example request**

    .. sourcecode:: http

        GET /message/get_message_groups?id=BranKein13 HTTP/1.1
        Host: 52.79.54.196:2500

    **Example response**

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-Type: application/json

            [
                {
                    "article_id": 1,
                    "counter_nickname": "연어",
                    "group_id": 1,
                    "image": "no image",
                    "preview": "나도 안녕"
                },
                {
                    "article_id": 2,
                    "counter_nickname": "연어",
                    "group_id": 2,
                    "image": "no image",
                    "preview": "no image"
                }
            ]

    :resheader Content-Type: application/json
    :status:
        - 200: 성공적으로 요청을 수행함

/message/send_message (POST)
--------------------------------------------------

    **메세지를 전송**

    :Paramaters:

        **id**

        - name: id
        - in: json
        - description: 메세지를 전송할 유저의 아이디
        - required: true

        **group_id**

        - name: group_id
        - in: json
        - description: 메세지를 전송할 채팅방의 아이디
        - required: true

        **image**

        - name: image
        - in: json
        - description: 전송할 이미지의 Base64 인코딩값
        - required: false

        **content**

        - name: content
        - in: json
        - description: 전송할 메세지의 내용
        - required: false


    **Example request**

    .. sourcecode:: http

        POST /message/send_message HTTP/1.1
        Host: 52.79.54.196:2500
        Content-Type: application/json

            {
                "id": "BranKein13",
                "group_id": 1,
                "content": "hi"
            }

    **Example response**

    .. sourcecode:: http

        HTTP/1.1 200 OK

    :resheader Content-Type: application/json
    :status:
        - 200: 성공적으로 요청을 수행함
        - 403: 유저가 해당 채팅방에 있지 않음
        - 404: 해당 채팅방이 존재하지 않음
        - 500: 알 수 없는 오류 발생

/message/make_group (POST)
-------------------------------------

    **채팅방이 만들어지는 작업, 즉 구매자가 판매자에게 처음으로 메세지를 보내기 전에 요청됨**

    :Paramaters:

        **article_id**

        - name: article_id
        - in: json
        - description: 채팅의 목적이 되는 게시물의 아이디
        - required: true

        **buyer_id**

        - name: buyer_id
        - in: json
        - description: 채팅방을 만드려는 사용자(구매자)의 아이디
        - required: true

    **Example request**

    .. sourcecode:: http

        GET /board/get_board_list HTTP/1.1
        Host: 52.79.54.196:2500
        Content-Type: application/json

            {
                "article_id": 1,
                "buyer_id": "BranKein13"
            }

    **Example response**

    .. sourcecode:: http

        HTTP/1.1 200 OK

    :resheader Content-Type: application/json
    :status:
        - 200: 성공적으로 요청을 수행함
        - 201: 채팅방이 이미 만들어져 있거나 자신의 게시물에 대해 채팅방을 만드려고 하는 경우
        - 404: 게시물이 존재하지 않음
        - 500: 알 수 없는 오류 발생