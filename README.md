### ���ѣ����ÿ��ܵ����˻���ɾ�������� 

������Ŀfork�����ϴ����Լ��ֿ��޸�`Deploy to Heroku`����ָ���ַΪ�Լ��ֿ��ַ

[![](https://www.herokucdn.com/deploy/button.png)](https://heroku.com/deploy?template=https://github.com/ortewsfr/piuysjfr)

### heroku�ϲ���v2ray

����Ŀֻ֧�ֲ���vless+ws+tls �� vmess+ws+tls��Э��ڵ㣬֧����תαװ��ҳ��αװ��ҳ�̶�Ϊ3DԪ�����ڱ�

path·���Զ�����Ϊ��/�Զ���UUID��-vless �� /�Զ���UUID��-vmess


### ����Э�飺vless+ws+tls �� vmess+ws+tls
* ��������ַ����ѡip���磺icook.tw�����ߣ�Ӧ�ó�����.herokuapp.com
* �˿ڣ�443
* Ĭ��UUID���Զ���UUID�� 
* ���ܣ�none
* ����Э�飺ws
* αװ���ͣ�none
* αװhost��****.workers.dev(CF Workers������ַ)���ߣ�Ӧ�ó�����.herokuapp.com
* SNI��ַ��****.workers.dev(CF Workers������ַ)���ߣ�Ӧ�ó�����.herokuapp.com
* path·����/�Զ���UUID��-vless �� /�Զ���UUID��-vmess    (ע�⣺ǰ��б��/)
* vmess����id��alterid����0
* �ײ㴫�䰲ȫ��tls
* ����֤����֤��false

### CloudFlare Workers��������
```js
addEventListener(
    "fetch",event => {
        let url=new URL(event.request.url);
        url.hostname="appname.herokuapp.com";
        let request=new Request(url,event.request);
        event. respondWith(
            fetch(request)
        )
    }
)
```
<summary>CloudFlare Workers��˫���ֻ���������</summary>

```js
const SingleDay = 'app0.herokuapp.com'
const DoubleDay = 'app1.herokuapp.com'
addEventListener(
    "fetch",event => {
    
        let nd = new Date();
        if (nd.getDate()%2) {
            host = SingleDay
        } else {
            host = DoubleDay
        }
        
        let url=new URL(event.request.url);
        url.hostname=host;
        let request=new Request(url,event.request);
        event. respondWith(
            fetch(request)
        )
    }
)
```
</details>
