---
title: "容器類別::swap | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- swap method
ms.assetid: 898c219c-bc8e-4d14-a149-6240426c693f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 62acdf7bf8278dfba3cf85bc9d5ced26a0f3fcea
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="container-classswap"></a>容器類別::swap
> [!NOTE]
>  本主題位於 Visual C++ 文件內，可做為 C++ 標準程式庫中所用容器的無作用範例。 如需詳細資訊，請參閱 [C++ 標準程式庫容器](../standard-library/stl-containers.md)。  
  
會交換 **\*this** 和其引數之間受控制的序列。  
  
## <a name="syntax"></a>語法  
  
```  
void swap(Container& right);
```  
  
## <a name="remarks"></a>備註  
若為 **\*this.get\_allocator ==** _right_**.get_allocator**，則會在固定的時間進行交換。 否則，它會執行多個元素指派，和與兩個受控制序列中元素數目成正比的建構函式呼叫。  
  
## <a name="see-also"></a>請參閱  
[範例容器類別](../standard-library/sample-container-class.md)
