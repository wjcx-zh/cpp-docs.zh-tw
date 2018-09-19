---
title: 記錄捲動 （MFC 資料存取） 的命令處理常式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- record views [C++], scrolling
- record scrolling [C++]
- scrolling records
ms.assetid: f8b13477-2a37-459e-a30c-806fb78165ac
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b51a6e9c9cf9516ed86066f712a17fea69c3cb50
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46112235"
---
# <a name="command-handlers-for-record-scrolling--mfc-data-access"></a>記錄捲動的命令處理常式 (MFC 資料存取)

[CRecordView](../mfc/reference/crecordview-class.md)類別會提供預設命令處理下列標準命令：  
  
- ID_RECORD_MOVE_FIRST  
  
- ID_RECORD_MOVE_LAST  
  
- ID_RECORD_MOVE_NEXT  
  
- ID_RECORD_MOVE_PREV  
  
`OnMove`成員函式提供預設命令處理所有的四個命令，將記錄間移動。 發出這些命令時，RFX (或 DFX) 會將新的記錄載入記錄集的欄位，DDX 則將值移到記錄表單的控制項中。 如需 RFX 的詳細資訊，請參閱[資料錄欄位交換 (RFX)](../data/odbc/record-field-exchange-rfx.md)。  
  
> [!NOTE]
>  請務必為與標準記錄巡覽命令相關聯的任何使用者介面物件，使用這些標準命令 ID。  
  
## <a name="see-also"></a>另請參閱  

[支援資料錄檢視的瀏覽](../data/supporting-navigation-in-a-record-view-mfc-data-access.md)