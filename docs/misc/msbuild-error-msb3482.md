---
title: "MSBuild 錯誤 MSB3482 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.SignFile.SignToolError"
helpviewer_keywords: 
  - "MSB3482"
ms.assetid: fd09371f-2658-4534-affa-edb485575f1a
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB3482
**MSB3482: 簽署時發生錯誤: '\<錯誤\>'。**  
  
 當您使用 ClickOnce 部署發行或使用 SignTool 簽署資訊清單時，可能會遇到這個錯誤，這個錯誤是由 SignTool 所產生。 以下列出常見的問題。  
  
 **簽署時發生錯誤: '值不能為 null。 參數名稱: strongNameKey'。**  
  
 這個問題可能會在 ClickOnce 部署期間出現於錯誤清單中。 此問題是因為選取無效的簽署金鑰。 通常會發生於您嘗試使用未經 RSA 加密的金鑰時。 SignTool 只支援 RSA 金鑰加密。  
  
 若要更正這個錯誤，請取得已啟用程式碼簽署的 RSA 加密金鑰。  
  
 **簽署時發生錯誤: '無法建立憑證鏈結到受信任的根授權單位'。**  
  
 這個問題可能會在 ClickOnce 部署期間出現於錯誤清單中。 此問題是因為憑證具有使用者電腦上不信任的鏈結或根授權單位。 通常會發生於在電腦之間移動憑證\/金鑰時。  
  
 若要更正這個錯誤，請安裝建立該憑證之憑證授權單位 \(CA\) 的「根憑證」。 一般而言，您可以視需要移至 CA 廠商的網站以重新下載。  
  
 **簽署時發生錯誤: '無法簽署 ...\\setup.exe。 SignTool 錯誤: ISignCode::Sign 傳回錯誤: 0x80880253 簽署者的憑證無法用於簽署。'**  
  
 這個問題可能會在 ClickOnce 部署期間出現於錯誤清單中。  
  
 此問題最有可能是因為憑證不在有效日期內；例如，如果您擁有過期的憑證。  
  
 若要更正這個錯誤，請取得具有有效日期的更新憑證。  
  
 有關如何更新憑證的相關資訊，請參閱 Microsoft 知識庫 \([http:\/\/support.microsoft.com](http://support.microsoft.com/kb/925521)\) 文章 925521＜用於簽署安裝的憑證過期後，嘗試更新 Visual Studio 2005 ClickOnce 應用程式時，會收到錯誤訊息＞。  
  
 **機碼組不存在。**  
  
 .pfx 檔與憑證可能不符。 請嘗試刪除並重新安裝憑證及\/或重新建立 .pfx 檔。  
  
 **機碼用在特定狀態時無效**  
  
 請參閱 http:\/\/blogs.msdn.com\/b\/smondal\/archive\/2012\/05\/08\/an\-error\-occurred\-while\-signing\-key\-not\-valid\-for\-use\-in\-specified\-state.aspx  
  
 **'參數不正確。**  
  
 您的組建是否正在服務中執行，或者位於與匯入憑證的使用者帳戶不同的使用者帳戶中？ 請嘗試關閉任何需要私密金鑰保護的本機安全性原則設定。  接著，刪除並重新匯入組建之使用者帳戶的憑證。  
  
 **無法完成所要求的操作。  電腦必須受信任才能委派，且目前的使用者帳戶必須設定為允許委派。**  
  
 請參閱[這篇 MSDN 部落格文章](http://technet.microsoft.com/en-us/library/cc782684\(v=ws.10\).aspx)。  
  
## 請參閱  
 [程式碼簽署簡介](https://msdn.microsoft.com/en-us/library/ms537361\(v=vs.85\).aspx)   
 [SignTool.exe \(Sign Tool\)](../Topic/SignTool.exe%20\(Sign%20Tool\).md)   
 [專案設計工具、簽署頁](../Topic/Signing%20Page,%20Project%20Designer.md)   
 [如何：簽署組件 \(Visual Studio\)](http://msdn.microsoft.com/zh-tw/f468a7d3-234c-4353-924d-8e0ae5896564)   
 [如何：使用強式名稱簽署組件](../Topic/How%20to:%20Sign%20an%20Assembly%20with%20a%20Strong%20Name.md)   
 [強式名稱的組件](../Topic/Strong-Named%20Assemblies.md)   
 [Managed 應用程式的強式名稱簽署](http://msdn.microsoft.com/zh-tw/5fef3490-c519-4363-94fd-8b1ad260dab5)   
 [\<PackageFiles\> 項目](../Topic/%3CPackageFiles%3E%20Element%20\(Bootstrapper\).md)