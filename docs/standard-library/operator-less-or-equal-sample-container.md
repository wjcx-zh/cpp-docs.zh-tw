---
title: "operator&lt;= (&lt;範例容器&gt;) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- std::<=
- std.operator<=
- operator<=
- std.<=
- std::operator<=
- <=
dev_langs: C++
helpviewer_keywords:
- operator<=
- operator <=
- <= operator, with specific objects
- <= operator
ms.assetid: 338577dd-dc88-4a2b-9e12-0379c54fc8a2
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ecedf4f43ed9aafaf3eebfe5c05a87ee32d2e4cc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="operatorlt-ltsample-containergt"></a>operator&lt;= (&lt;範例容器&gt;)
> [!NOTE]
>  本主題位於 Visual C++ 文件內，可做為 C++ 標準程式庫中所用容器的無作用範例。 如需詳細資訊，請參閱 [C++ 標準程式庫容器](../standard-library/stl-containers.md)。  
  
 多載 **operator<=** 來比較樣板類別 [Container](../standard-library/sample-container-class.md) 的兩個物件。  
  
## <a name="syntax"></a>語法  
  
```  
template <class Ty>  
bool operator<=(
    const Container <Ty>& left,  
    const Container <Ty>& right);
```  
  
## <a name="return-value"></a>傳回值  
 傳回 `!(right < left)`。  
  
## <a name="see-also"></a>另請參閱  
 [\<範例容器>](../standard-library/sample-container.md)

