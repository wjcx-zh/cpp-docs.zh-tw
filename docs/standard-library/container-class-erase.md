---
title: "容器類別::erase | Microsoft Docs"
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
- erase method
ms.assetid: abc091c5-5a80-4bd8-93a8-a2d9bde2efec
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: aeb81554bdc50db44e9e8d4ee66369149eceb875
ms.contentlocale: zh-tw
ms.lasthandoff: 04/04/2017

---
# <a name="container-classerase"></a>容器類別::erase
> [!NOTE]
>  本主題為 Visual C++ 文件中 C++ 標準程式庫所用容器的無作用範例。 如需詳細資訊，請參閱 [C++ 標準程式庫容器](../standard-library/stl-containers.md)。  
  
 插入元素。  
  
## <a name="syntax"></a>語法  
  
```  
 
    iterator erase(
    iterator _Where);

iterator erase(
    iterator first,  
    iterator last);
```  
  
## <a name="remarks"></a>備註  
 第一個成員函式中移除指向受控制序列的項目*_Where*。 第二個成員函式會移除 [`first`, `last`) 範圍中受控制序列中的元素。 兩者皆會傳回迭代器，其指定任何移除的元素之後的第一個剩餘元素；如果沒有這個元素，則為 [end](../standard-library/container-class-end.md)。  
  
 只有當複製作業擲回例外狀況時，成員函式才會擲回例外狀況。  
  
## <a name="see-also"></a>另請參閱  
 [範例容器類別](../standard-library/sample-container-class.md)

