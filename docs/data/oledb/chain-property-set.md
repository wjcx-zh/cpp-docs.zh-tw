---
title: CHAIN_PROPERTY_SET |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CHAIN_PROPERTY_SET
dev_langs:
- C++
helpviewer_keywords:
- CHAIN_PROPERTY_SET macro
ms.assetid: 2bcf6d7d-f4e5-480d-9140-1e32a0994c94
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9db57535f3f0bc7653c80b83c3e0115727eed707
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33094331"
---
# <a name="chainpropertyset"></a>CHAIN_PROPERTY_SET
這個巨集鏈結在一起，屬性群組。  
  
## <a name="syntax"></a>語法  
  
```cpp
CHAIN_PROPERTY_SET(ChainClass)  
  
```  
  
#### <a name="parameters"></a>參數  
 *ChainClass*  
 [in]鏈結屬性類別的名稱。 這是已包含的對應 （例如工作階段、 命令或資料來源物件類別） 的 ATL 專案精靈所產生的類別。  
  
## <a name="remarks"></a>備註  
 您可以鏈結至您自己的類別，從另一個類別屬性集，然後直接從您的類別存取內容。  
  
> [!CAUTION]
>  謹慎地使用這個巨集。 不當使用，可能會導致失敗的 OLE DB 一致性測試取用者。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB 提供者範本的巨集](../../data/oledb/macros-for-ole-db-provider-templates.md)