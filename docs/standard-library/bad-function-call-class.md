---
title: "bad_function_call 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- functional/std::bad_function_call
dev_langs:
- C++
helpviewer_keywords:
- bad_function_call class
ms.assetid: b70a0268-43ff-4f3b-a283-faf1cb172d4c
caps.latest.revision: 20
author: corob-msft
ms.author: corob
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
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: c6aa47c6eb3d9fc39eed6b68856641cd86d27ba5
ms.contentlocale: zh-tw
ms.lasthandoff: 10/03/2017

---
# <a name="badfunctioncall-class"></a>bad_function_call 類別
報告錯誤的函式呼叫。  
  
## <a name="syntax"></a>語法  
  
```  
class bad_function_call  
 : public std::exception {  
 };  
```  
  
## <a name="remarks"></a>備註  
 此類別描述所擲回的例外狀況，表示對 [function 類別](../standard-library/function-class.md)的 `operator()` 呼叫。

