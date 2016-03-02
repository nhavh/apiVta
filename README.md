
DANH SÁCH SẢN PHẨM NỔI BẬT
********************


API này cho phép lấy tất cả các sản phẩm của trang chủ được cấu hình từng sản phẩm.

Request


HTTP Request
------------

    GET http://10.10.40.171/product-api/HomeProductMobis

Header
------


    Content-Type:application/json

    
    
LOGIN
-----
Hành động đăng nhập vào hệ thống của Vật Giá

Sau khi login thành công, hệ thống sẽ trả về ID của user đăng nhập, cần lưu ID này để truyền lên trong quá trình cập nhật tồn kho

Mẫu JSON.


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

|   Thuộc tính   | Giá trị |                  Mô tả                   |
| -------------- |:-------:| ----------------------------------------:|
| database_name  | string  | Tên database của vật giá                 |
| user_name      | string  | Tên đăng nhập                            |
| password       | string  | Mật khẩu đăng nhập                       |

Output

Sau khi đăng nhập thành công, thông tin trả về có dạng

    {
        "jsonrpc": "2.0",
        "result": "id_user"
    }

|   Thuộc tính   | Giá trị |                  Mô tả                   |
| -------------- |:-------:| ----------------------------------------:|
| id_user        | int     | ID trả về sau khi đăng nhập thành công   |

    
CẬP NHẬT TỒN KHO
-----

Mẫu JSON.

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


|   Thuộc tính   | Giá trị |                  Mô tả                   |
| -------------- |:-------:| ----------------------------------------:|
| database_name  | string  | Tên database của vật giá                 |
| id_user        | int     | id_user trả về sau khi đăng nhập         |
| data           | object  | Dữ liệu import. Xem tại :ref:`data'      |





.. _data:

Data

Mẫu JSON.

    {
      "supplier_product_code": "qty",
      "supplier_product_code": "qty",
    }


|   Thuộc tính         | Giá trị |                  Mô tả                   |
| -------------------- |:-------:| ----------------------------------------:|
|supplier_product_code | string  | Mã sản phẩm của Viễn Thông A             |
| qty                  | int     | Số lượng tồn kho                         |





Output

    return {
        "code": 200,
        "message": "Success",
    }


THÔNG TIN API
=============

|   Thuộc tính         | Giá trị                       |                  Mô tả                   |
| -------------------- |:-----------------------------:| ----------------------------------------:|
|database_name         | prod-v2                       | Tên database                             |
| user_name            | vienthongastore               | Tên đăng nhập                            |
| password             | d2,v(uJX!@cFB8KHNM4G3GUme=,r8]| Mật khẩu đăng nhập                       |

Example

Request

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

    {
        "jsonrpc": "2.0",
        "result": 43
    }

    
