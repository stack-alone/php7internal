#一、基本变量

zval  ： （可以表示php内的任意变量）
      定义
           例子：
 ```          
     struct _zval_struct {
       zend_value        value;                 /* value */
       union {
             struct {
                    ZEND_ENDIAN_LOHI_3(
                           zend_uchar    type,               /* active type */
                           zend_uchar    type_flags,
                           union {
                                 uint16_t  call_info;    /* call info for EX(This) */
                                 uint16_t  extra;        /* not further specified */
                           } u)
             } v;
             uint32_t type_info;
       } u1;
       union {
             uint32_t     next;                 /* hash collision chain */
             uint32_t     cache_slot;           /* cache slot (for RECV_INIT) */
             uint32_t     opline_num;           /* opline number (for FAST_CALL) */
             uint32_t     lineno;               /* line number (for ast nodes) */
             uint32_t     num_args;             /* arguments number for EX(This) */
             uint32_t     fe_pos;               /* foreach position */
             uint32_t     fe_iter_idx;          /* foreach iterator index */
             uint32_t     access_flags;         /* class constant access flags */
             uint32_t     property_guard;       /* single property guard */
             uint32_t     constant_flags;       /* constant flags */
             uint32_t     extra;                /* not further specified */
       } u2;
};
```

总大小：value：8字节,u1和u2个4个字节。总大小16个字节,zend_value:是联合体
          
```          
typedef union _zend_value {
       zend_long         lval;        //整型                 /* long value */
       double            dval;        //浮点型                 /* double value */
       zend_refcounted  *counted;
       zend_string      *str;//字符串
       zend_array       *arr;//数组
       zend_object      *obj;//对象
       zend_resource    *res;//资源型
       zend_reference   *ref;//引用型
       zend_ast_ref     *ast;
       zval             *zv;
       void             *ptr;
       zend_class_entry *ce;//类
       zend_function    *func;//函数
       struct {
             uint32_t w1;
             uint32_t w2;
       } ww;
} zend_value;
```