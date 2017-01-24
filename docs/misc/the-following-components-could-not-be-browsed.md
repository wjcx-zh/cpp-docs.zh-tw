---
title: "The following components could not be browsed: | Microsoft Docs"
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
  - "VS_E_CANNOTBROWSECOM"
  - "VS.Message.0x00006A6D"
  - "VS_E_LOADTYPELIBFAILED"
  - "VS_E_INVALIDCOMCOMPONENT"
  - "VS_E_UNRECOGNIZEDCOMPONENT"
  - "VS.Message.0x00006A6E"
  - "VS.Message.ObjectBrowserErrors"
  - "vs.Message.0x00005AC3"
  - "VS.Message.0x00005AC4"
  - "VS.Message.0x00005AC5"
  - "VS_E_REGFAILEDCOMCOMPONENT"
ms.assetid: 83b03767-eecb-47a4-8029-166308c7dded
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The following components could not be browsed:
這個訊息方塊可以列出與物件瀏覽器和 \[元件選擇\] 對話方塊相關的許多錯誤。  以下是最常見的一些錯誤。  
  
## 無法在物件瀏覽器中檢視元件或檔案類型。  
 通常是指定了不存在或無效的檔名，或者檔案無法透過物件瀏覽器瀏覽時，就會發生這種錯誤。  
  
#### 若要更正這個錯誤  
  
-   請確認您指定的檔名存在，而且是可瀏覽的元件 \(例如 .NET 組件 \(Assembly\)、COM 型別程式庫或來源瀏覽器檔\)。  
  
## 檔案不是有效的 .NET Framework 或 COM 元件。  
 通常是指定的元件並非 .NET Framework 組件或 COM 型別程式庫時就會發生這種錯誤。  
  
#### 若要更正這個錯誤  
  
-   選擇其他要瀏覽的元件。  
  
## 無法登錄檔案為 COM 元件。  
 這個錯誤通常在 COM 元件的型別程式庫不能註冊時發生。  該型別程式庫可能不存在或可能已損毀。  
  
#### 若要更正這個錯誤  
  
-   請重新安裝此元件，然後再試一次。  
  
## 沒有登錄相符的型別程式庫，或者登錄的資訊無效。  
 您指定的型別程式庫已經不存在，或者未包含有效的資訊。  
  
#### 若要更正這個錯誤  
  
-   請確認型別程式庫存在，而且已正確登錄。  
  
## 遺漏瀏覽 COM 型別程式庫所需的元件或目前尚未註冊。  
 vstlbinf.dll 檔案遺漏，或者未正確登錄。  
  
#### 若要修正此問題  
  
1.  找出您電腦上的 vstlbinf.dll，使用 regsvr32.exe 登錄。  
  
     \-或\-  
  
2.  如果在您的電腦上找不到 vstlbinf.dll，請重新安裝此產品。  
  
## 請參閱  
 [Object Browser](http://msdn.microsoft.com/zh-tw/f89acfc5-1152-413d-9f56-3dc16e3f0470)   
 [Edit Custom Component Set Dialog Box](http://msdn.microsoft.com/zh-tw/dc995bd7-afbf-4389-ba1c-f377b677ded7)