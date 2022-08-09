## 搜索框 
    form	
        经 Form.create() 包装过的组件会自带 this.form 属性，如果使用 template 语法，
    可以使用 this.$form.createForm(this, options)
   
    1.搜索框上绑定form表单数据，作为存放搜索信息的对象  
        <a-form layout="horizontal" :form="form" ref="searchRef"

    2.data里面创建form对象，使用函数对其进行赋值
        form: this.$form.createForm(this),

    validateFields	
        校验并获取一组输入域的值与 Error，若 fieldNames 参数为空，则校验全部组件
        *两个参数：Error，values        Error用于校验form里面的值   values用于拿到当前form里面的值

    3.通过官方函数方法拿到form里面的值    
        this.form.validateFields((err, values) => {
            console.log(values)//打印form里面的值
        })

