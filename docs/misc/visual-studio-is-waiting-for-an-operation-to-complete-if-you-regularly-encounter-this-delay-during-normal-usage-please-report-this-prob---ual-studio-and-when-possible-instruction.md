---
title: "Visual Studio is waiting for an operation to complete. If you regularly encounter this delay during normal usage please report this problem to Microsoft. Please include a description of the work you’re doing in Visual Studio and when possible instruction | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.VB_E_IDWOLEBUSY"
  - "vs.message.0x800A002B"
ms.assetid: 688fdf7e-c3ef-41f1-bc22-9f88f8f5b353
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Visual Studio is waiting for an operation to complete. If you regularly encounter this delay during normal usage please report this problem to Microsoft. Please include a description of the work you’re doing in Visual Studio and when possible instruction
伺服器應用程式忙碌中，無法完成目前的要求。  
  
 此錯誤也可能是因防毒軟體封鎖某些 devenv.exe 處理程序而造成。  產品中有幾種功能是使用指令碼，而防毒軟體可能封鎖了這些指令碼。  如需相關資訊，請線上參閱＜PRB：啟動 Visual IDE 後並未開啟，或者出現「應用程式無法啟動」錯誤訊息＞，位置在 [http:\/\/support.microsoft.com\/default.aspx?scid\=kb;en\-us;306905&Product\=vsnet](http://support.microsoft.com/default.aspx?scid=kb;en-us;306905&Product=vsnet)。  
  
### 若要修正伺服器應用程式相關的錯誤  
  
1.  請選擇 \[切換至\]，開啟應用程式並調查原因。  
  
     \-或\-  
  
     選擇 \[重試\]，等待伺服器應用程式完成處理要求。  
  
     \-或\-  
  
     選擇 \[取消\]，結束要求。  
  
### 若要修正防毒相關錯誤  
  
-   在您的防毒軟體中，指定軟體允許源自於 devenv.exe 的指令碼可以執行。  如需詳細指示，請參閱防毒軟體的產品文件。