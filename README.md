web - android ��Ͽ���

js����java�����ַ�ʽ:
1.ֱ����URL��������Զ���Э��
2.��js��ʹ��Prompt��ʾ��

java�����

���ɲ���:

        //����WebView���ԣ��ܹ�ִ��Javascript�ű�
        WebSettings settings = webView.getSettings();
        settings.setJavaScriptEnabled(true);
        //ʵ���������� ������ַ�������
        Interceptor interceptor = new Interceptor(this, new DistributManage() {
            @Override
            public JSAction onIntercept(HashMap<String, String> param) {
                String name = param.get("name");
                JSAction jsAction = null;
                switch (name) {
                    case "��ť1":
                        jsAction = new JSPrint1();
                        break;
                    case "��ť2":
                        jsAction = new JSPrint2();
                        break;
                }
                return jsAction;
            }
        }, new InterceptorConfig());
        //����Prompt��ʾ������
        webView.setWebChromeClient(new HybridWebChromeClient(interceptor));
        //����URL����
        webView.setWebViewClient(new HybridWebClient(interceptor));
