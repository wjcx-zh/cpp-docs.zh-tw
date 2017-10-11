---
title: "編譯器警告 C4687 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4687
dev_langs:
- C++
helpviewer_keywords:
- C4687
ms.assetid: 2f28e0b1-7358-4c88-bd70-aad8f0aa004c
caps.latest.revision: 5
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 266213deba94bdc925747d57dee184aca5f5f605
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-warning-c4687"></a>編譯器警告 C4687
'class': 密封抽象類別不能實作介面 'interface'  
  
 密封的抽象類別通常是僅用來存放靜態成員函式。  
  
 如需詳細資訊，請參閱[抽象](../../windows/abstract-cpp-component-extensions.md)和[密封](../../windows/sealed-cpp-component-extensions.md)。  
  
 根據預設，C4687 會發出為錯誤。 您可以隱藏與 C4687[警告](../../preprocessor/warning.md)pragma。 如果您確定您想要在密封的抽象類別中實作的介面，您可以隱藏 C4687。  
  
## <a name="example"></a>範例  
 下列範例會產生 C4687。  
  
```  
// C4687.cpp  
// compile with: /clr /c  
interface class A {};  
  
ref struct B sealed abstract : A {};   // C4687  
ref struct C sealed : A {};   // OK  
ref struct D abstract : A {};   // OK  
```
