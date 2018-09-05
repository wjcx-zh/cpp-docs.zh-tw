---
title: CString 語意 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- semantics in Cstring
- CString objects, assignment semantics
- assignment statements, assigning CString objects
ms.assetid: d4023480-526f-499a-85f6-324b4de5b85f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 256c71cace15a3906ac048819ab2ffdef2071ff4
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43761269"
---
# <a name="cstring-semantics"></a>CString 語意

即使[CString](../atl-mfc-shared/reference/cstringt-class.md)物件所能成長的動態物件，其作用類似內建基本類型和簡單的類別。 每個`CString`物件都代表唯一的值。 `CString` 物件應該視為實際的字串，而不是字串的指標。

您可以指派其中`CString`到另一個物件。 不過，當您修改兩個`CString`物件，另`CString`未修改物件，如下列範例所示：

[!code-cpp[NVC_ATLMFC_Utilities#188](../atl-mfc-shared/codesnippet/cpp/cstring-semantics_1.cpp)]

請注意，在範例中，這兩個`CString`物件被視為 「 等於 」，因為它們代表相同的字元字串。 `CString`類別會多載等號比較運算子 (`==`) 來比較兩個`CString`物件根據其值 （內容） 而不是他們的身分識別 （位址）。

## <a name="see-also"></a>另請參閱

[字串 (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)

