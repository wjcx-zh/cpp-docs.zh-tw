---
title: 範例容器成員 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- container classes
ms.assetid: dc5a1998-a31b-4adf-b888-8abe5b87a4e0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7c844416151874714aa86a2ffe9762949c6a62a3
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="sample-container-members"></a>範例容器成員

> [!NOTE]
> 本主題位於 Visual C++ 文件內，可做為 C++ 標準程式庫中所用容器的無作用範例。 如需詳細資訊，請參閱 [C++ 標準程式庫容器](../standard-library/stl-containers.md)。

## <a name="reference"></a>參考資料

## <a name="typedefs"></a>Typedefs

|||
|-|-|
|[const_iterator](../standard-library/container-class-const-iterator.md)|描述的物件可作為受控制序列的常數迭代器。|
|[const_reference](../standard-library/container-class-const-reference.md)|描述的物件可作為受控制序列之項目的常數參考。|
|[const_reverse_iterator](../standard-library/container-class-const-reverse-iterator.md)|描述的物件可作為受控制序列的常數反向迭代器。|
|[difference_type](../standard-library/container-class-difference-type.md)|描述的物件可代表受控制序列中任兩個項目位址之間的差距。|
|[iterator](../standard-library/container-class-iterator.md)|描述的物件可作為受控制序列的迭代器。|
|[reference](../standard-library/container-class-reference.md)|描述的物件可作為受控制序列的項目參考。|
|[reverse_iterator](../standard-library/container-class-reverse-iterator.md)|描述的物件可作為受控制序列的反向迭代器。|
|[size_type](../standard-library/container-class-size-type.md)|描述的物件可代表任何受控制序列的長度。|
|[value_type](../standard-library/container-class-value-type.md)|作為 **Ty** 樣板參數的同義字。|

## <a name="member-functions"></a>成員函式

|||
|-|-|
|[begin](../standard-library/container-class-begin.md)|傳回迭代器，指向序列的第一個項目 (或空序列結尾以外的位置)。|
|[clear](../standard-library/container-class-clear.md)|呼叫 [erase](../standard-library/container-class-erase.md)( [begin](../standard-library/container-class-begin.md), [end](../standard-library/container-class-end.md))。|
|[empty](../standard-library/container-class-empty.md)|對空的受控制序列傳回 **true**。|
|[end](../standard-library/container-class-end.md)|傳回指向序列結尾之外的迭代器。|
|[erase](../standard-library/container-class-erase.md)|清除項目。|
|[max_size](../standard-library/container-class-max-size.md)|傳回物件可控制的最長序列長度 (不論受控制序列的長度為何，且為定時的狀態)。|
|[rbegin](../standard-library/container-class-rbegin.md)|傳回指向受控制序列結尾之外的反向迭代器，並指定反向序列的開頭。|
|[rend](../standard-library/container-class-rend.md)|成員函式會傳回反向迭代器，指向序列的第一個項目 (或空序列結尾以外的位置)，並指定反向序列的結尾。|
|[size](../standard-library/container-class-size.md)|傳回受控制序列的長度 (不論受控制序列的長度為何，且為定時的狀態)。|
|[swap](../standard-library/container-class-swap.md)
