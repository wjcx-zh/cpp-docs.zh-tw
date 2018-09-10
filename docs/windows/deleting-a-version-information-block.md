---
title: 刪除版本資訊區塊 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.version
dev_langs:
- C++
helpviewer_keywords:
- blocks, deleting
- version information, deleting blocks
- resources [C++], deleting version information
ms.assetid: 4e1641eb-d5b2-4183-b273-bc5b51af1537
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b3d7a3b64a612000eb25f2f72cd289caf7692f7b
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44314998"
---
# <a name="deleting-a-version-information-block-c"></a>刪除版本資訊區塊 （c + +）

### <a name="to-delete-a-version-information-block"></a>刪除版本資訊區塊

1. 按兩下版本資訊資源圖示，在 [資源檢視](../windows/resource-view-window.md)中開啟它。

   > [!NOTE]
   > 如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。

2. 以滑鼠右鍵按一下您想要刪除的區塊標頭，然後從快顯功能表選擇 [刪除版本資訊區塊]  。

   這個命令會刪除選取的標頭，而剩餘的版本資訊則保留不動。 請注意您無法復原此動作。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[版本資訊編輯器](../windows/version-information-editor.md)  
[版本資訊 (Windows)](https://msdn.microsoft.com/library/windows/desktop/ms646981.aspx)