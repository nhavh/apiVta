CẬP NHẬT TỒN KHO SẢN PHẨM
********************


API này cho phép Viễn Thông A cập nhật số lượng tồn kho của sản phẩm sang Vật Giá.

Quá trình cập nhật tồn kho sẽ trải qua 2 bước

1. Login để lấy user_id

2. Cập nhật tồn kho


Request
=======


HTTP Request
------------


::

    POST http://odoo.vnpid.com/jsonrpc

Header
------


::

    Content-Type:application/json

    
    
LOGIN
-----
Hành động đăng nhập vào hệ thống của Vật Giá

Sau khi login thành công, hệ thống sẽ trả về ID của user đăng nhập, cần lưu ID này để truyền lên trong quá trình cập nhật tồn kho

Mẫu JSON.
"""""""

.. code-block:: json

    {
        "jsonrpc":"2.0",
        "method":"call",
        "params":{
            "service":"common",
            "method":"login",
            "args":[
                "database_name",
                "user_name",
                "password"
                ]
            }
    }

+----------------+---------+------------------------------------------+
|   Thuộc tính   | Giá trị |                  Mô tả                   |
+================+=========+==========================================+
| database_name  | string  | Tên database của vật giá                 |
+----------------+---------+------------------------------------------+
| user_name      | string  | Tên đăng nhập                            |
+----------------+---------+------------------------------------------+
| password       | string  | Mật khẩu đăng nhập                       |
+----------------+---------+------------------------------------------+

Output
""""""
Sau khi đăng nhập thành công, thông tin trả về có dạng

.. code-block:: json

    {
        "jsonrpc": "2.0",
        "result": "id_user"
    }

+----------------+---------+------------------------------------------+
|   Thuộc tính   | Giá trị |                  Mô tả                   |
+================+=========+==========================================+
| id_user        | int     | ID trả về sau khi đăng nhập thành công   |
+----------------+---------+------------------------------------------+

    
CẬP NHẬT TỒN KHO
-----

Mẫu JSON.
""""""

.. code-block:: json

    {
    "jsonrpc":"2.0",
    "method":"call",
    "params":{
            "service":"object",
            "method":"execute",
            "args":[
                        "database_name",
                        "id_user",
                        "password",
                        "vta.store",
                        "update_qty_vta_store",
                        "data"
                    ]
            }
    }

+----------------+---------+------------------------------------------+
|   Thuộc tính   | Giá trị |                  Mô tả                   |
+================+=========+==========================================+
| database_name  | string  | Tên database của vật giá                 |
+----------------+---------+------------------------------------------+
| id_user        | int     | id_user trả về sau khi đăng nhập         |
+----------------+---------+------------------------------------------+
| data           | object  | Dữ liệu import. Xem tại :ref:`data'      |
+----------------+---------+------------------------------------------+


.. _data:

Data
""""

Mẫu JSON.

.. code-block:: json

    {
      "supplier_product_code": "qty",
      "supplier_product_code": "qty",
    }

+----------------------+---------+------------------------------------------+
|   Thuộc tính         | Giá trị |                  Mô tả                   |
+======================+=========+==========================================+
|supplier_product_code | string  | Mã sản phẩm của Viễn Thông A             |
+----------------------+---------+------------------------------------------+
| qty                  | int     | Số lượng tồn kho                         |
+----------------------+---------+------------------------------------------+


Output
""""""

.. _Thành công

.. code-block:: json

    return {
        "code": 200,
        "message": "Success",
    }


.. _Không thành công

.. code-block:: json

    return {
        "code": 400,
        "error": {
            "type": "ecls",
            "message": "emsg",
        }
    }

THÔNG TIN API
=============
+----------------------+-------------------------------+------------------------------------------+
|   Thuộc tính         | Giá trị                       |                  Mô tả                   |
+======================+===============================+==========================================+
|database_name         | prod-v2                       | Tên database                             |
+----------------------+-------------------------------+------------------------------------------+
| user_name            | vienthongastore               | Tên đăng nhập                            |
+----------------------+-------------------------------+------------------------------------------+
| password             | d2,v(uJX!@cFB8KHNM4G3GUme=,r8]| Mật khẩu đăng nhập                       |
+----------------------+-------------------------------+------------------------------------------+

Example
=======

Login
-----

Request
"""""""

.. code-block:: json

    {
        "jsonrpc":"2.0",
        "method":"call",
        "params":{
            "service":"common",
            "method":"login",
            "args":[
                "prod-v2",
                "vienthongastore",
                "d2,v(uJX!@cFB8KHNM4G3GUme=,r8]"
                ]
            }
    }
    
Output
""""""

.. code-block:: json

    {
        "jsonrpc": "2.0",
        "result": 43
    }

Cập nhật tồn kho
---------------

Request
"""""""

.. code-block:: json

    {
    "jsonrpc":"2.0",
    "method":"call",
    "params":{
            "service":"object",
            "method":"execute",
            "args":[
                        "prod-v2",
                        43,
                        "d2,v(uJX!@cFB8KHNM4G3GUme=,r8]",
                        "vta.store",
                        "update_qty_vta_store",
                        {"70049851" : 4,"70049859" : 5}
                    ]
            }
    }
    
Output
""""""

.. code-block:: json

    return {
        "code": 200,
        "message": "Success",
    }

    
