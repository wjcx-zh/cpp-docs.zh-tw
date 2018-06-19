---
title: jitintrinsic |Microsoft 文件
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
ms.openlocfilehash: 71cd88882ea104275e4c1a43ccf05494a859d303
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32418750"
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