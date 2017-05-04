---
title: "IntPtr::op_explicit 運算子 | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::IntPtr::op_explicit"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IntPtr::op_explicit 方法"
ms.assetid: cc52e9d5-fe73-471b-8cff-d9f684ba6e20
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# IntPtr::op_explicit 運算子
將指定的參數轉換為 IntPtr，或將指標轉換為 IntPtr 值。  
  
## 語法  
  
```cpp  
static IntPtr::operator IntPtr( void* value1);   static IntPtr::operator IntPtr( int value2);   static IntPtr::operator void*( IntPtr value3 );  
```  
  
#### 參數  
 value1  
 控制代碼的指標或 IntPtr。  
  
 value2  
 可以轉換為 IntPtr 的 32 位元整數。  
  
 value3  
 IntPtr。  
  
## 傳回值  
 第一個和第二個運算子傳回 IntPtr。 第三個運算子傳回目前 IntPtr 所表示的值的指標。  
  
## 需求  
 **最低支援用戶端：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **最低支援伺服器：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空間：**Platform  
  
 **中繼資料：**platform.winmd  
  
## 請參閱  
 [Platform::IntPtr 實值類別](../cppcx/platform-intptr-value-class.md)