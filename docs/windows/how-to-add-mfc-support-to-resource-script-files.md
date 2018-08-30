---
title: 如何： 將 MFC 支援新增至資源指令碼檔案 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.resvw.add.MFC
dev_langs:
- C++
helpviewer_keywords:
- rc files, adding MFC support
- .rc files, adding MFC support
- MFC, adding support to resource scripts files
- resource script files, adding MFC support
ms.assetid: 599dfe9d-ad26-4e34-899c-49b56599e37f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f84f343a5a742e37deb776f20c9038ea7f90576e
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43198431"
---
# <a name="how-to-add-mfc-support-to-resource-script-files"></a>如何：將 MFC 支援加入至資源指令碼檔

一般來說，當您建置 MFC 應用程式使用 Windows [MFC 應用程式精靈](../mfc/reference/mfc-application-wizard.md)，精靈會產生一組基本的檔案 （包括資源指令碼 (.rc) 檔），其中包含 Microsoft Foundation 的核心功能類別 (MFC)。 不過，如果您要為不以 MFC 為基礎的 Windows 應用程式編輯 .rc 檔，則無法使用 MFC 架構的下列特定功能：

- MFC 程式碼精靈 (先前稱為 「[MFC ClassWizard](https://msdn.microsoft.com/98dc2434-ba93-4e0b-b084-1a4bc26cdf1e)")

- 功能表提示字串

- 下拉式方塊控制項的清單內容

- ActiveX 控制項裝載

不過，您可以將 MFC 支援加入至沒有該支援的現有 .rc 檔。

### <a name="to-add-mfc-support-to-rc-files"></a>將 MFC 支援加入至 .rc 檔

1. 開啟資源指令碼檔案。

   > [!NOTE]
   > 如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。

2. 在 [資源檢視](../windows/resource-view-window.md)，反白顯示 [資源] 資料夾 (例如，MFC.rc)。

3. 在 [[屬性] 視窗](/visualstudio/ide/reference/properties-window)，將**MFC 模式**屬性設 **，則為 True**。

   > [!NOTE]
   > 除了設定這個旗標外，.rc 檔必須是 MFC 專案的一部分。 比方說，就是直接設定**MFC 模式**要 **，則為 True** .rc 檔案是在 Win32 專案將不會提供您任何 MFC 功能。

## <a name="requirements"></a>需求

MFC

## <a name="see-also"></a>另請參閱

[資源檔](../windows/resource-files-visual-studio.md)  
[資源編輯器](../windows/resource-editors.md)