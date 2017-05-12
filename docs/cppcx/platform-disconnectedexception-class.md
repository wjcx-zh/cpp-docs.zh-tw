---
title: "Platform::DisconnectedException 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::DisconnectedException"
  - "Platform/Platform::DisconnectedException::DisconnectedException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::DisconnectedException"
ms.assetid: c25e0d64-5bff-4c21-88e5-c4ec2776fa7f
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 4
---
# Platform::DisconnectedException 類別
當 COM Proxy 物件嘗試參考已不存在的 COM 伺服器時會擲回  
  
## 語法  
  
```  
public ref class DisconnectedException : COMException,    IException,    IPrintable,    IEquatable  
```  
  
## 備註  
 當類別 A 參考另一個處理序中的其他類別 \(類別 B\) 時，類別 A 需要 Proxy 物件，才能與保留類別 B 之跨處理序的 COM 伺服器通訊。有時候伺服器記憶體用盡，但類別 A 卻不知道。 在這種情況下，會擲回 RPC\_E\_DISCONNECTED 例外狀況，並轉譯成 Platform::DisconnectedException。 發生這種情形的情境之一，就是事件來源叫用的委派已傳遞給它，但在它訂閱事件之後的某個時間點，該委派卻終結。 發生此情況時，事件來源會將委派從其引動過程清單中移除。  
  
 如需詳細資訊，請參閱 [COMException](../cppcx/platform-comexception-class.md) 類別。  
  
## 需求  
 **最低支援用戶端：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **最低支援伺服器：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空間：**Platform  
  
 **中繼資料：**platform.winmd  
  
## 請參閱  
 [Platform::COMException 類別](../cppcx/platform-comexception-class.md)