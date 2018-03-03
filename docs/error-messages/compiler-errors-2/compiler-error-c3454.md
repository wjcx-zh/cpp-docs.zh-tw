---
title: "編譯器錯誤 C3454 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3454
dev_langs:
- C++
helpviewer_keywords:
- C3454
ms.assetid: dc4e6d57-5b4d-4114-8d6f-22f9ae62925b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 42a685d7084f5edd2a3f6b2fe6f1ab9d83e9c18f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3454"></a>編譯器錯誤 C3454
類別宣告上不允許 [attribute]  
  
 必須定義類別，它才能是屬性。  
  
 如需詳細資訊，請參閱 [attribute](../../windows/attribute.md)。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3454。  
  
```  
// C3454.cpp  
// compile with: /clr /c  
using namespace System;  
  
[attribute]   // C3454  
ref class Attr1;  
  
[attribute]   // OK  
ref class Attr2 {};  
```