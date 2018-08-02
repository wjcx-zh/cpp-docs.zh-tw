---
title: virtual （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- virtual_cpp
- virtual
dev_langs:
- C++
helpviewer_keywords:
- virtual base classes [C++], declaring
- base classes [C++], virtual
- virtual functions [C++], declaring
- virtual keyword [C++]
ms.assetid: c2eb987d-6cf3-43b6-aa0c-29a6f561b1ae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 84035f2007f3c45c33c1dfa342caf5c788580205
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/02/2018
ms.locfileid: "39460915"
---
# <a name="virtual-c"></a>virtual (C++)
**虛擬**關鍵字會宣告虛擬函式或虛擬基底類別。  
  
## <a name="syntax"></a>語法  
  
```  
virtual [type-specifiers] member-function-declarator  
virtual [access-specifier] base-class-name  
```  
  
#### <a name="parameters"></a>參數  
 *類型規範*  
 指定虛擬成員函式的傳回型別。  
  
 *成員函式宣告子*  
 宣告成員函式。  
  
 *存取規範*  
 基底類別，定義存取層級**公用**，**保護**或是**私人**。 可以出現在前後**虛擬**關鍵字。  
  
 *基底類別名稱*  
 識別先前宣告的類別類型。  
  
## <a name="remarks"></a>備註  
 請參閱[虛擬函式](../cpp/virtual-functions.md)如需詳細資訊。  
  
 另請參閱下列關鍵字：[類別](../cpp/class-cpp.md)，[私人](../cpp/private-cpp.md)，[公用](../cpp/public-cpp.md)，以及[保護](../cpp/protected-cpp.md)。  
  
## <a name="see-also"></a>另請參閱  
 [關鍵字](../cpp/keywords-cpp.md)