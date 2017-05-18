---
title: "嚴重錯誤 C1016 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C1016
dev_langs:
- C++
helpviewer_keywords:
- C1016
ms.assetid: 33f45c3e-2d8f-43ad-a445-c412d1d54ce1
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: b7f9a620f3df21a737736fce943ee750c7171387
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="fatal-error-c1016"></a>嚴重錯誤 C1016
\#ifdef 必須是識別項 #ifndef 必須是識別項  
  
 條件式編譯指示詞 ([#ifdef](../../preprocessor/hash-ifdef-and-hash-ifndef-directives-c-cpp.md)或`#ifndef`) 來評估沒有識別碼。 若要解決這個錯誤，請指定識別項。  
  
 下列範例會產生 C1016：  
  
```  
// C1016.cpp  
#ifdef   // C1016  
#define FC1016  
#endif  
  
int main() {}  
```  
  
 可能的解決方式：  
  
```  
// C1016b.cpp  
#ifdef X  
#define FC1016  
#endif  
  
int main() {}  
```
