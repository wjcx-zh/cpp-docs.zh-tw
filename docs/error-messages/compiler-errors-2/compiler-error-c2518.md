---
title: "編譯器錯誤 C2518 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2518
dev_langs: C++
helpviewer_keywords: C2518
ms.assetid: a7895b47-da90-4851-ac97-18e81479595a
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2a76c528def49b1235460fa4d6632efd196417d3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2518"></a>編譯器錯誤 C2518
關鍵字 'keyword' 在基底類別清單; 中不合法忽略  
  
 關鍵字`class`和`struct`不應該出現在基底類別清單。  
  
 下列範例會產生 C2518:  
  
```  
// C2518.cpp  
// compile with: /c  
class B {};  
class C : public class B {};   // C2518  
class D: public B {};   // OK  
```