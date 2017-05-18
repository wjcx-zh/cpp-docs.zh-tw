---
title: "operator&gt; (&lt;範例容器&gt;) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- std::operator>
- std.>
- std.operator>
- operator>
- std::>
- '>'
dev_langs:
- C++
helpviewer_keywords:
- '> operator, comparing specific objects'
- operator >
ms.assetid: 49bd417a-3305-4ffa-9884-39d3904ed87d
caps.latest.revision: 9
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
ms.openlocfilehash: 275ee24409172a344bbbaf7a526fe5f0c1390edb
ms.contentlocale: zh-tw
ms.lasthandoff: 04/04/2017

---
# <a name="operatorgt-ltsample-containergt"></a>operator&gt; (&lt;範例容器&gt;)
> [!NOTE]
>  本主題位於 Visual C++ 文件內，可做為 C++ 標準程式庫中所用容器的無作用範例。 如需詳細資訊，請參閱 [C++ 標準程式庫容器](../standard-library/stl-containers.md)。  
  
 多載 **operator>** 來比較樣板類別 [Container](../standard-library/sample-container-class.md) 的兩個物件。  
  
## <a name="syntax"></a>語法  
  
```  
template <class Ty>  
bool operator*gt;(
    const Container <Ty>& left,  
    const Container <Ty>& right);
```  
  
## <a name="return-value"></a>傳回值  
 傳回 `right < left`。  
  
## <a name="see-also"></a>另請參閱  
 [\<範例容器>](../standard-library/sample-container.md)


