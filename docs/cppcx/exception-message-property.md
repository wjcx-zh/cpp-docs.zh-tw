---
title: "Exception::Message 屬性 | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::Exception::Message"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Exception::Message 屬性"
ms.assetid: ad1199cd-0889-4803-ad0d-a3a7b3c51891
caps.latest.revision: 10
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Exception::Message 屬性
描述錯誤的訊息。  
  
## 語法  
  
```cpp  
public:property String^ Message;  
```  
  
## 屬性值  
 針對肇因於 Windows 執行階段的例外狀況，這是系統提供的錯誤說明。  
  
## 備註  
 在 [!INCLUDE[win8](../cppcx/includes/win8-md.md)] 中，這個屬性是唯讀的，因為在該版本的 Windows 執行階段中，例外狀況只做為 HRESULTS 跨 ABI 傳輸。 在 [!INCLUDE[win81](../cppcx/includes/win81-md.md)] 中，跨 ABI 傳輸更豐富的例外狀況資訊，而且您可以提供其他元件可透過程式設計方式存取的自訂訊息。 如需詳細資訊，請參閱[例外狀況 \(C\+\+\/CX\)](../cppcx/exceptions-c-cx.md)。  
  
## 需求  
 **最低支援用戶端：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **最低支援伺服器：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空間：**Platform  
  
 **中繼資料：**platform.winmd  
  
## 請參閱  
 [Platform::Exception 類別](../cppcx/platform-exception-class.md)