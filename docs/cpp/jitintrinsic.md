---
title: jitintrinsic |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- jitintrinsic
- jitintrinsic_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], jitintrinsic
- jitintrinsic __declspec modifier
ms.assetid: 23dbe416-7ef6-442b-b16d-9a81aab04fa6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f8b1c932f53651b8ad116139724348714b183506
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2018
ms.locfileid: "37939386"
---
# <a name="jitintrinsic"></a>jitintrinsic
將函式標記為 64 位元 Common Language Runtime 的必要項。 這種方式會在 Microsoft 所提供程式庫中的某些函式上使用。  
  
## <a name="syntax"></a>語法  
  
```  
__declspec(jitintrinsic)  
```  
  
## <a name="remarks"></a>備註  
 `jitintrinsic` 會將 MODOPT (<xref:System.Runtime.CompilerServices.IsJitIntrinsic>) 加入至函式簽章。  
  
 不建議使用此使用者 **__declspec**修飾詞為非預期的結果可能會發生。  
  
## <a name="see-also"></a>另請參閱  
 [__declspec](../cpp/declspec.md)   
 [關鍵字](../cpp/keywords-cpp.md)