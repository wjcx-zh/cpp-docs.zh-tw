---
title: "CString 語意 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
helpviewer_keywords:
- semantics in Cstring
- CString objects, assignment semantics
- assignment statements, assigning CString objects
ms.assetid: d4023480-526f-499a-85f6-324b4de5b85f
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 394e459a46003e3f1baccff7dd4c76f40b73e354
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cstring-semantics"></a>CString 語意
即使[CString](../atl-mfc-shared/reference/cstringt-class.md)物件所能成長的動態物件，它們做為內建基本類型和簡單的類別。 每個`CString`物件都代表唯一的值。 `CString`物件應該想像成實際的字串，而不是字串的指標。  
  
 您可以指派其中**CString**到另一個物件。 不過，當您修改兩個`CString`物件的其他`CString`未修改物件，如下列範例所示：  
  
 [!code-cpp[NVC_ATLMFC_Utilities#188](../atl-mfc-shared/codesnippet/cpp/cstring-semantics_1.cpp)]  
  
 此範例中的，請注意，這兩個`CString`物件被視為 「 等於 」，因為它們代表相同的字元字串。 `CString`類別會多載等號比較運算子 (`==`) 比較兩個`CString`物件而不是其身分識別 （位址） 為基礎的值 （內容）。  
  
## <a name="see-also"></a>請參閱  
 [字串 (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)

