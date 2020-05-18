# SDK Android Conexa Saúde


### 1 – Instalação  
Clone ou faça download do release do nosso SDK no GitHub

#### 1.1 Importar os módulos ao seu projeto
- conexasdk.aar 
- mobilertc.aar 

#### 1.2 Selecione “New Module” “Import .JAR/AAR Package”: 
 
#### 1.3 Adicionar dependências necessárias


```
dependencies { 
  implementation 'androidx.constraintlayout:constraintlayout:1.1.3' 
  implementation 'com.google.android.material:material:1.0.0-rc01' 
 
  // Conexa dependencies 
  implementation project(':conexasdk') 
  implementation project(':mobilertc') 
} 
```

IMPORTANTE:
- Atualizar seu projeto Android para ser um projeto AndroidX
- Futuras atualizações sobreescrever os arquivos .aar nos diretórios correspondentes. 

 

### 2 – Utilização

#### 2.1 Importar o framework

```
import br.com.conexasdk.ConexaSDK 
```
 

#### 2.2 – Implementação do SDK
Chamar método abaixo passando as seguintes informações: 


Kotlin 

```
var conexa = ConexaSDK(context) 
conexa.startMeeting(meetingNo, meetingPassword,  displayName) 
```

Java 

```
ConexaSDK conexa = new ConexaSDK(context); 
conexa.startMeeting(meetingNo, meetingPassword,  displayName); 
```
 

#### 2.3 – Implementação do SDK utilizando callback. 

Kotlin 
```
var conexa = ConexaSDK(context, object : ConexaSDK.OnMeetingListener { 
    override fun onErrorStartMeeting(message:String, errorCode:Int, internalErrorCode:Int){ 

    } 

    override fun onMeetingStatusChanged(status: MeetingStatus, code: Int){ 

    } 

}) 

conexa.startMeeting(meetingNo, meetingPassword , displayName) 
```

Java 

```
ConexaSDK conexa = new ConexaSDK(context, new ConexaSDK.OnMeetingListener() { 
    @Override 
    public void onErrorStartMeeting(String message, int errorCode, int internalErrorCode) { 
    //
    } 

    @Override 
    public void onMeetingStatusChanged(MeetingStatus status, int code) { 
    //
    } 

}); 

conexa.startMeeting(meetingNo, meetingPassword , displayName); 
```
 
- meetingNo (número da reunião): obrigatório 
- meetingPassword (password da reunião): opcional 
- displayName (nome do participante): opcional 
