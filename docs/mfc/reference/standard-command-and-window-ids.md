---
title: 標準命令和視窗 Id |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros
dev_langs:
- C++
helpviewer_keywords:
- standard command and Window IDs
ms.assetid: 0424805c-fff8-4531-8f0c-15cfb13aa612
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 218f0b87edd2ec8c846c08e5cdc72aa01e22c0b1
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2018
ms.locfileid: "37886020"
---
# <a name="standard-command-and-window-ids"></a>標準命令和視窗 ID
MFC 程式庫在 Afxres.h 中定義了數種標準命令和視窗 ID。 這些 ID 最常用在資源編輯器以及 [屬性] 視窗中，以將訊息對應至處理函式。 所有標準的命令都有**ID_** 前置詞。 比方說，當您使用功能表編輯器時，您通常要繫結檔案開啟的功能表項目至標準 ID_FILE_OPEN 命令識別碼。  
  
 對於大部分的標準命令，應用程式程式碼不需要參照命令 ID，因為架構本身會處理透過其要主架構類別中的訊息對應命令 (`CWinThread`， `CWinApp`， `CView`， `CDocument`，及等等）。  
  
 除了標準命令 Id 之外的其他標準 Id 數目會定義具有前置詞的**AFX_ID**。 這些 Id 包含標準視窗 Id (前置詞**AFX_IDW_**)，字串 Id (前置詞**AFX_IDS_**)，以及數種其他類型。  
  
 識別碼開頭**AFX_ID**程式設計人員而言，很少使用的前置詞，但您可能需要參考這些 Id 時覆寫同樣參考架構函式**AFX_ID**s。  
  
 此參考中沒有個別記錄的 ID。 您可以在技術附註中找到更多有關[20](../../mfc/tn020-id-naming-and-numbering-conventions.md)， [21](../../mfc/tn021-command-and-message-routing.md)，並[22](../../mfc/tn022-standard-commands-implementation.md)。  
  
> [!NOTE]
>  標頭檔 Afxres.h 間接包含在 Afxwin.h 中。 您必須在應用程式的資源指令碼 (.rc) 檔中明確包含下列陳述式：  
  
 [!code-cpp[NVC_MFC_Utilities#47](../../mfc/codesnippet/cpp/standard-command-and-window-ids_1.h)]  
  
## <a name="see-also"></a>另請參閱  
 [巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)
