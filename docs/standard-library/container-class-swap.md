---
title: "容器類別::swap | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- swap method
ms.assetid: 898c219c-bc8e-4d14-a149-6240426c693f
caps.latest.revision: 8
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
translationtype: Machine Translation
ms.sourcegitcommit: f293f074f2b8e2334dc70fbebba8e6f4c17efecc
ms.openlocfilehash: 33ec601dcc8d32b85c2c38ed3fc5a07842a056fc
ms.lasthandoff: 02/24/2017

---
# <a name="container-classswap"></a>容器類別::swap
> [!NOTE]
>  本主題為 Visual C++ 文件中 C++ 標準程式庫所用容器的無作用範例。 如需詳細資訊，請參閱 [C++ 標準程式庫容器](../standard-library/stl-containers.md)。  
  
會交換 **\*this** 和其引數之間受控制的序列。  
  
## <a name="syntax"></a>語法  
  
```  
void swap(Container& right);
```  
  
## <a name="remarks"></a>備註  
若為 **\*this.get\_allocator ==** _right_**.get_allocator**，則會在固定的時間進行交換。 否則，它會執行多個元素指派，和與兩個受控制序列中元素數目成正比的建構函式呼叫。  
  
## <a name="see-also"></a>另請參閱  
[範例容器類別](../standard-library/sample-container-class.md)

