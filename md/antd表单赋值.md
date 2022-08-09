### 标签绑定数据
    1. data定义： form: this.$form.createForm(this),
    2. a-from标签绑定from
       <a-form layout="horizontal" :form="form" ref="searchRef"></a-from>
    3.  元素绑定：v-decorator="['id']"    其中id为绑定的属性名
#### 给标签赋值
    const fields = ["id","name","country","product_id","open_time","start_time","end_time","content",];
    created() {
    // 防止表单未注册
    fields.forEach((v) => this.form.getFieldDecorator(v));
    // 当 model 发生改变时，为表单设置值
    this.$watch("modules", () => {
        this.modules && this.form.setFieldsValue(this.modules);
    });
    },

### 表单验证
    //子组件  Son_form
    <Son_form  :visible="visible"   :isTitle="isTitle"  ref="articleRef"   @cancel="handleCancel"
    :loading="confirmLoading"  @ok="handleOk"  :modules="modules" />
    //简易版
    <Son_form ref="articleRef" :modules="modules" />

#### methods中定义方法可以打印出当前所有的表单值：
    const formRef = this.$refs.articleRef;                     拿到子组件节点
    const form = formRef.form;                                赋值
    this.form.validateFields((err, values) => {             配套函数，err验证是否通过  values  form数据
                    console.log("values", values)
                })

    this.$refs?.formRef?.form.resetFields();                 清空form 数据
#### 详解：
    this.$refs?---方法名     .formRef?---子组件绑定ref名      
    .form---子组件data里面数据名      .resetFields(）---清空form里卖弄数据的函数

#### 表单验证规则：
    <a-form-item
        label="国家"
        :labelCol="{ span: 6 }"      
        :wrapperCol="{ span: 15, offset: 1 }"
    >
        <a-input
        placeholder="请输入国家"
        allowClear
        v-decorator="[
            'country',
            {
            rules: [
                {
                required: true,
                message: '请输入国家',
                },
            ],
            },
        ]"
        />
    </a-form-item>