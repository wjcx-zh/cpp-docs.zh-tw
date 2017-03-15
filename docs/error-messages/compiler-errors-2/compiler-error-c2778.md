---
title: "編譯器錯誤 C2778 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2778"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2778"
ms.assetid: b24cb732-2914-42cc-8928-e2d87b393428
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 編譯器錯誤 C2778
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\_\_declspec\(uuid\(\)\) 產生的 GUID 不適當  
  
 提供了不正確的 GUID 給 [uuid](../../cpp/uuid-cpp.md) 擴充屬性。  
  
 GUID 必須是符合下列格式的十六進位數字字串：  
  
```  
// C2778a.cpp  
// compile with: /c  
struct __declspec(uuid("00000000-0000-0000-0000-000000000000")) A {};  
struct __declspec(uuid("{00000000-0000-0000-0000-000000000000}")) B{};  
```  
  
 `uuid` 擴充屬性接受 [CLSIDFromString](http://msdn.microsoft.com/library/windows/desktop/ms680589) 可辨識的字串 \(使用或不使用括號區隔符號皆可\)。  
  
 下列範例會產生 C2778：  
  
```  
// C2778b.cpp  
struct __declspec(uuid(" 00000000-0000-0000-0000-000000000000 ")) C { };   // C2778  
struct __declspec(uuid("00000000000000000000000000000000")) D { };   // C2778  
```