---
title: "編譯器警告 (層級 1) C4912 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4912"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4912"
ms.assetid: ba1f1a66-8c20-4792-9ac8-43e49f729ae2
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4912
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'attribute': 屬性在巢狀 UDT 上有未定義的行為，可能受到忽略  
  
 套用至巢狀 UDT \(使用者定義類型，可以是 typedef、等位或結構\) 的屬性可能會被忽略。  
  
 下列程式碼示範如何產生這個警告：  
  
```  
// C4912.cpp // compile with: /W1 #include <windows.h> [emitidl, module(name="xx")]; [object, uuid("00000000-0000-0000-0000-000000000002")] __interface IMy { }; [coclass, default(IMy), appobject, uuid("00000000-0000-0000-0000-000000000001")] class CMy : public IMy { [export, v1_enum] typedef enum myEnum { k3_1 = 1, k3_2 = 2 } myEnumv;   // C4912 }; int main() { }  
```