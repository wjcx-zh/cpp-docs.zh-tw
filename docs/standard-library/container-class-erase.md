---
title: "容器類別::erase | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: erase method
ms.assetid: abc091c5-5a80-4bd8-93a8-a2d9bde2efec
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ef45ec608736640f8f17a375838d3778d3ecc9b7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="container-classerase"></a>容器類別::erase
> [!NOTE]
>  本主題位於 Visual C++ 文件內，可做為 C++ 標準程式庫中所用容器的無作用範例。 如需詳細資訊，請參閱 [C++ 標準程式庫容器](../standard-library/stl-containers.md)。  
  
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
  
## <a name="see-also"></a>請參閱  
 [範例容器類別](../standard-library/sample-container-class.md)
