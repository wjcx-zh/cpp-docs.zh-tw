---
title: "StringReference::StringReference 建構函式 | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vccorlib/Platform::StringReference::StringReference"
dev_langs: 
  - "C++"
ms.assetid: 87dd9201-e638-4913-b37c-7091ae3f91ea
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# StringReference::StringReference 建構函式
初始化 `StringReference` 類別的新執行個體。  
  
## 語法  
  
```cpp  
  
    StringReference();  
  
   StringReference(const StringReference& __fstrArg)  
  
StringReference(const ::default::char16* __strArg)  
  
StringReference(const ::default::char16* __strArg, size_t __lenArg)  
```  
  
#### 參數  
 `__fstrArg`  
 其資料用來初始化新執行個體的 `StringReference`。  
  
 `__strArg`  
 用來初始化新執行個體之 char16 值陣列的指標。  
  
 `__lenArg`  
 `__strArg` 中的元素數目。  
  
## 備註  
 此建構函式的第一個版本是預設建構函式。 第二個版本會從 `StringReference` 參數指定的物件初始化新的 `__fstrArg` 執行個體類別。 第三和第四個多載會從 char16 值的陣列初始化新的 `StringReference` 執行個體。 char16 表示 16 位元的 UNICODE 文字字元。  
  
## 需求  
 **最低支援用戶端：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **最低支援伺服器：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空間：**Platform  
  
 **標頭：**vccorlib.h  
  
## 請參閱  
 [Platform::StringReference 類別](../cppcx/platform-stringreference-class.md)