---
title: "取代 (STL/CLR) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::replace
dev_langs: C++
helpviewer_keywords: replace function [STL/CLR]
ms.assetid: 3792abca-8d73-476a-8540-c5f739aa48c2
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: fe1f9cf94f39deb2a8db662a149a625b035b8567
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="replace-stlclr"></a>replace (STL/CLR)
檢查範圍內的每個項目，如果符合指定的值則予以取代。  
  
## <a name="syntax"></a>語法  
  
```  
template<class _FwdIt, class _Ty> inline  
    void replace(_FwdIt _First, _FwdIt _Last,  
        const _Ty% _Oldval, const _Ty% _Newval);  
```  
  
## <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`replace`。 如需詳細資訊，請參閱[取代](../standard-library/algorithm-functions.md#replace)。  
  
## <a name="requirements"></a>需求  
 **標頭：** \<演算法 cliext/>  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>請參閱  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)