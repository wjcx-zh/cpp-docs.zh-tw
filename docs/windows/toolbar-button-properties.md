---
title: 工具列按鈕屬性 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- size, toolbar buttons
- toolbar buttons (in Toolbar editor), setting properties
- Toolbar editor, toolbar button properties
- status bars, active toolbar button text
- command IDs, toolbar buttons
- width, toolbar buttons
ms.assetid: b2705814-7c5d-4f24-8f77-07559b0cdda2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3e61ba7e8720c755ce26408826c56a5c1fc9d51e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33890673"
---
# <a name="toolbar-button-properties"></a>工具列按鈕屬性
工具列按鈕的屬性包括：  
  
|屬性|描述|  
|--------------|-----------------|  
|**ID**|定義按鈕的識別碼。 下拉式清單提供常用**識別碼**名稱。|  
|**寬度**|設定按鈕的寬度。 建議使用 16 個像素。|  
|**高度**|設定按鈕的高度。 請注意一個按鈕的高度變更工具列上的所有按鈕的高度。 建議 15 像素。|  
|**提示**|定義顯示在狀態列中的訊息。 加入 \n 和名稱將以工具提示加入至工具列按鈕。 如需詳細資訊，請參閱[建立工具提示](../windows/creating-a-tool-tip-for-a-toolbar-button.md)。|  
  
 **寬度**和**高度**套用於所有按鈕。 用來建立工具列點陣圖的最大寬度為 2048年。 因此如果您將按鈕寬度為 512，只能有四個按鈕，如果您將寬度設 513 時，您只能有三個按鈕。  
  
 如需將資源加入至 managed 專案的詳細資訊，請參閱[桌面應用程式中的資源](/dotnet/framework/resources/index)中 *.NET Framework 開發人員手冊 》。* 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理應用程式的資源上的資訊，請參閱[全球化和當地語系化的.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。  
  
## <a name="requirements"></a>需求  
 MFC 或 ATL  
  
## <a name="see-also"></a>另請參閱  
 [變更工具列按鈕屬性](../windows/changing-the-properties-of-a-toolbar-button.md)   
 [工具列編輯器](../windows/toolbar-editor.md)

