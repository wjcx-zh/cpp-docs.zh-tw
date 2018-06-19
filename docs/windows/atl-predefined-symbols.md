---
title: ATL 預先定義的符號 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- symbols, ATL predefined
- ATL symbols
ms.assetid: 60d8f4e6-6ed9-47f3-9051-e4bf34384456
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7c00487b2bb7c7a67dfb81ffb638f5a46fc611bc
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33863734"
---
# <a name="atl-predefined-symbols"></a>ATL 預先定義的符號
ATL 標頭檔中定義這些符號，但是它們可以支援標準的 Windows 應用程式函式和動作。 這些符號主要用於對話方塊。 當您正在使用的對話方塊和控制項中[對話方塊編輯器](../windows/dialog-editor.md)，這些符號會出現在 通用控制項相關聯的 [屬性] 視窗。 比方說，如果您的對話方塊具有 [取消] 按鈕，該命令會與相關聯的符號 IDCANCEL 中[屬性 視窗](/visualstudio/ide/reference/properties-window)。  
  
|||  
|-|-|  
|IDABORT|控制： 對話方塊的 [中止] 按鈕|  
|IDC_STATIC|靜態控制項的控制項：|  
|IDCANCEL|控制： 對話方塊的 [取消] 按鈕|  
|IDIGNORE|控制： 對話方塊的 [略過] 按鈕|  
|IDNO|控制項： 對話方塊沒有按鈕|  
|IDOK|控制項： 對話方塊 [確定] 按鈕|  
|IDR_ACCELERATOR1|資源： 快速鍵對應表|  
|IDRETRY|控制： 對話方塊的 [重試] 按鈕|  
|IDS_PROJNAME|目前應用程式名稱字串：|  
|IDYES|控制： 對話方塊 [是] 按鈕|  
  
## <a name="requirements"></a>需求  
 ATL  
  
## <a name="see-also"></a>另請參閱  
 [預先定義的符號 Id](../windows/predefined-symbol-ids.md)   
 [符號：資源識別項](../windows/symbols-resource-identifiers.md)