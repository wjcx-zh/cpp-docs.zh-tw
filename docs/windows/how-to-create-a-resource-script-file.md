---
title: 如何： 建立資源指令碼檔案 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- rc files [C++], creating
- .rc files [C++], creating
- resource script files [C++], creating
ms.assetid: 82be732a-cdcd-4a58-8de7-976d1418f86b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 32258a05cade33f20546acfc02b98370ada2b073
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46387129"
---
# <a name="how-to-create-a-resource-script-file-c"></a>如何： 建立資源指令碼檔案 （c + +）

> [!NOTE]
> **資源編輯器**不適用於 Express 版本。
>
> 這份資料適用於 Windows 桌面應用程式。 以 .NET 語言撰寫的專案不會使用資源指令碼檔。 如需詳細資訊，請參閱 [資源檔](../windows/resource-files-visual-studio.md)。

### <a name="to-create-a-new-resource-script-rc-file"></a>建立新的資源指令碼 (.rc) 檔

1. 將焦點放在您現有的專案資料夾中**方案總管**，例如`MyProject`。

   > [!NOTE]
   > 請勿混淆方案資料夾內專案資料夾**方案總管 中**。 如果您將焦點放在**解決方案**資料夾中，您的選擇中**加入新項目**對話方塊 （在步驟 3) 將會不同。

2. 在 [專案]  功能表中，按一下 [加入新項目] 。

3. 在 [加入新項目]  對話方塊中，按一下 [Visual C++]  資料夾，然後選擇右窗格中的 [資源檔 (.rc)]  。

4. 在 [名稱]  文字方塊中提供資源指令碼檔的名稱，然後按一下 [開啟] 。

您現在可以 [建立](../windows/how-to-create-a-resource.md) 新的資源並加入 .rc 檔中。

> [!NOTE]
> 您只能將資源指令碼 (.rc 檔) 加入已載入 Visual Studio IDE 的現有專案中， 而不能建立獨立的 .rc 檔 (即專案以外的檔案)。 [資源範本](../windows/how-to-use-resource-templates.md) (.rct 檔) 則可以隨時建立。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[資源檔](../windows/resource-files-visual-studio.md)<br/>
[資源編輯器](../windows/resource-editors.md)