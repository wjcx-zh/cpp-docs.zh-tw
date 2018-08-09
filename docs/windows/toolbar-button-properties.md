---
title: 工具列按鈕屬性 |Microsoft Docs
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
ms.openlocfilehash: a37e15c4235886eef1dbee958ec5c3da29caab0e
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39650114"
---
# <a name="toolbar-button-properties"></a>工具列按鈕屬性
工具列按鈕的屬性如下：  
  
|屬性|描述|  
|--------------|-----------------|  
|**ID**|定義按鈕的識別碼。 下拉式清單提供常見**識別碼**名稱。|  
|**寬度**|設定按鈕的寬度。 建議您使用 16 像素為單位。|  
|**高度**|設定按鈕的高度。 請注意一個按鈕的高度變更工具列上的所有按鈕的高度。 建議使用 15 像素為單位。|  
|**提示**|定義在狀態列中顯示的訊息。 加入 \n 和名稱加入至該工具列按鈕的工具提示。 如需詳細資訊，請參閱 <<c0> [ 建立工具提示](../windows/creating-a-tool-tip-for-a-toolbar-button.md)。|  
  
 **寬度**並**高度**適用於所有按鈕。 用來建立工具列點陣圖具有最大寬度為 2048年。 因此如果您可以設定按鈕的寬度設為 512，只能有四個按鈕，並將寬度設成 513，如果您只可以有三個按鈕。  
  
 如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。  
  
## <a name="requirements"></a>需求  
 MFC 或 ATL  
  
## <a name="see-also"></a>另請參閱  
 [變更工具列按鈕的屬性](../windows/changing-the-properties-of-a-toolbar-button.md)   
 [工具列編輯器](../windows/toolbar-editor.md)