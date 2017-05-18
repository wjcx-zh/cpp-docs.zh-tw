---
title: "標準命令和視窗 Id |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros
dev_langs:
- C++
helpviewer_keywords:
- standard command and Window IDs
ms.assetid: 0424805c-fff8-4531-8f0c-15cfb13aa612
caps.latest.revision: 13
author: mikeblome
ms.author: mblome
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
ms.sourcegitcommit: 5187996fc377bca8633360082d07f7ec8a68ee57
ms.openlocfilehash: d308f3f9efc5933124460d9839a0e94fffa60b4a
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="standard-command-and-window-ids"></a>標準命令和視窗 ID
MFC 程式庫在 Afxres.h 中定義了數種標準命令和視窗 ID。 這些 ID 最常用在資源編輯器以及 [屬性] 視窗中，以將訊息對應至處理函式。 所有標準命令都有**ID_**前置詞。 例如，當您使用功能表編輯器時，您通常要繫結檔案開啟的功能表項目至標準`ID_FILE_OPEN`命令 id。  
  
 對於大部分的標準命令，應用程式程式碼不會不需要參照命令 ID，因為架構本身會處理透過其要主架構類別中的訊息對應命令 ( `CWinThread`， `CWinApp`， `CView`， **CDocument**，依此類推)。  
  
 除了標準命令 Id 之外的其他標準 Id 的數目會定義具有前置詞的**AFX_ID**。 這些 Id 包含標準視窗 Id (前置詞**AFX_IDW_**)、 字串 Id (前置詞**AFX_IDS_**)，以及數個其他類型。  
  
 識別碼開頭的**AFX_ID**程式設計人員，很少使用的前置詞，但您可能需要覆寫同樣參考架構函式時，請參考這些 id **AFX_ID**s。  
  
 此參考中沒有個別記錄的 ID。 您可以找到更多有關在技術提示[20](../../mfc/tn020-id-naming-and-numbering-conventions.md)， [21](../../mfc/tn021-command-and-message-routing.md)，和[22](../../mfc/tn022-standard-commands-implementation.md)。  
  
> [!NOTE]
>  標頭檔 Afxres.h 間接包含在 Afxwin.h 中。 您必須在應用程式的資源指令碼 (.rc) 檔中明確包含下列陳述式：  
  
 [!code-cpp[NVC_MFC_Utilities #&47;](../../mfc/codesnippet/cpp/standard-command-and-window-ids_1.h)]  
  
## <a name="see-also"></a>另請參閱  
 [巨集和全域變數](../../mfc/reference/mfc-macros-and-globals.md)

