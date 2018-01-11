---
title: "operator&lt; (&lt;範例容器&gt;) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- std::operator<
- operator<
- std.<
- <
- std.operator<
- std::<
dev_langs: C++
helpviewer_keywords:
- < operator, comparing specific objects
- operator<, valarrays
- < operator
- operator <, valarrays
ms.assetid: 31027dd6-53be-428b-b950-1dcb25393597
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 554ceba328a0688ab11e7d66ece26204aad598e3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="operatorlt-ltsample-containergt"></a>operator&lt; (&lt;範例容器&gt;)
> [!NOTE]
>  本主題位於 Visual C++ 文件內，可做為 C++ 標準程式庫中所用容器的無作用範例。 如需詳細資訊，請參閱 [C++ 標準程式庫容器](../standard-library/stl-containers.md)。  
  
 多載 **operator<** 來比較樣板類別 [Container](../standard-library/sample-container-class.md) 的兩個物件。  
  
## <a name="syntax"></a>語法  
  
```  
template <class Ty>  
bool operator<(
    const Container <Ty>& left,  
    const Container <Ty>& right);
```  
  
## <a name="return-value"></a>傳回值  
 傳回 `lexicographical_compare(left.begin, left.end, right.begin, right.end)`。  
  
## <a name="see-also"></a>請參閱  
[\<範例容器>](../standard-library/sample-container.md)  
[begin](../standard-library/container-class-begin.md)  
[end](../standard-library/container-class-end.md)  