---
title: 預先定義的符號 Id |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- symbols, predefined IDs
- predefined symbol IDs
ms.assetid: 91a5d610-1a04-47e8-b8a4-63ad650a90df
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3c28d5d3d04bc48e7c79d634406d40292d869e36
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="predefined-symbol-ids"></a>預先定義的符號 ID
當您開始新的專案時，視專案類型而定，已預先定義一些符號 ID 供您使用。 這些符號 ID 支援各種程式庫和專案類型，例如 MFC。 它們代表通常包含在任何應用程式中的一般工作，或硬體項目 (如滑鼠或印表機) 的動作。  
  
 使用資源時，這些符號 ID 變得重要。 適用於當您編輯快速鍵對應表時；其中有些 ID 已與虛擬按鍵相關聯。 它們也可供您透過[屬性 視窗](/visualstudio/ide/reference/properties-window)。 您可以將任何預先定義的符號 ID 指派給新的資源，也可以將快速鍵指派給它們，而與符號 ID 相關聯的功能會自動與該按鍵組合相關聯。  
  
 這些程式庫有預先定義的符號，將顯示為專案的一部分：  
  
-   [MFC 預先定義的符號](../windows/mfc-predefined-symbols.md)  
  
-   [ATL 預先定義的符號](../windows/atl-predefined-symbols.md)  
  
-   [Win32 預先定義的符號](../windows/win32-predefined-symbols.md)  
  
    > [!NOTE]
    >  預先定義的符號一律是唯讀的。  
  

  
## <a name="requirements"></a>需求  
 Win32、MFC 或 ATL  
  
## <a name="see-also"></a>另請參閱  
 [符號：資源識別項](../windows/symbols-resource-identifiers.md)