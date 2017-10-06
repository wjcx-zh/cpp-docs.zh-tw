---
title: "jitintrinsic |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- jitintrinsic
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], jitintrinsic
- jitintrinsic __declspec modifier
ms.assetid: 23dbe416-7ef6-442b-b16d-9a81aab04fa6
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 6712a62aaff0ff903117da87364cae5bc88580fd
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="jitintrinsic"></a>jitintrinsic
將函式標記為 64 位元 Common Language Runtime 的必要項。 這種方式會在 Microsoft 所提供程式庫中的某些函式上使用。  
  
## <a name="syntax"></a>語法  
  
```  
__declspec(jitintrinsic)  
```  
  
## <a name="remarks"></a>備註  
 `jitintrinsic` 會將 MODOPT (<xref:System.Runtime.CompilerServices.IsJitIntrinsic>) 加入至函式簽章。  
  
 由於可能發生無法預期的結果，因此不建議使用者使用這個 `__declspec` 修飾詞。  
  
## <a name="see-also"></a>另請參閱  
 [__declspec](../cpp/declspec.md)   
 [關鍵字](../cpp/keywords-cpp.md)
