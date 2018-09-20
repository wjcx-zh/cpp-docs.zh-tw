---
title: 建立使用者無法結束的對話方塊中 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- dialog boxes [C++], creating
- modal dialog boxes [C++], logon screens
- logon screens
ms.assetid: 54823c27-1658-4388-bd12-0a1ce8f3899e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5abae461b4298d8a6300f5d7ad9f3e162a5b21c8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46447384"
---
# <a name="creating-a-dialog-box-c-that-users-cannot-exit"></a>建立對話方塊 （c + +），讓使用者無法結束

您可以建立使用者無法結束的執行階段對話方塊。 這種對話方塊對登入以及鎖定應用程式或文件非常實用。

### <a name="to-create-a-dialog-box-that-a-user-cannot-exit"></a>建立使用者無法結束的對話方塊

1. 在對話方塊的 [屬性]  窗格中，將 [系統功能表]  屬性設為 [false] 。

   這會停用對話方塊系統功能表並 [關閉]  按鈕。

2. 在對話方塊表單中，刪除 [取消]  和 [確定]  按鈕。

   在執行階段，使用者無法結束具有下列特性的強制回應對話方塊。

若要啟用這種對話方塊中的測試，測試對話方塊函式偵測到的時機**Esc**按下。 (**Esc**亦稱為 VK_ESCAPE 虛擬按鍵。)不論如何對話方塊中，設計來在執行階段行為，您可以終止它在測試模式中按下**Esc**。

> [!NOTE]
> 針對 MFC 應用程式，若要建立對話方塊，使用者無法結束，您必須覆寫預設行為`OnOK`並`OnCancel`因為即使刪除相關聯的按鈕時，對話方塊仍關閉按**請輸入**或是**Esc**。

如需有關如何將資源加入 managed 專案的資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[如何：建立資源](../windows/how-to-create-a-resource.md)<br/>
[資源檔](../windows/resource-files-visual-studio.md)<br/>
[對話方塊編輯器](../windows/dialog-editor.md)