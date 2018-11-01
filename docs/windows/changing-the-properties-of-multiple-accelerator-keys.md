---
title: 變更屬性的多個快速鍵 （c + +）
ms.date: 11/04/2016
helpviewer_keywords:
- keyboard shortcuts [C++], property changing
- accelerator tables [C++], changing properties
ms.assetid: b55c9bd6-b430-48bb-b942-0e6f21d7abf9
ms.openlocfilehash: 00c2bed34d70fa13161cbaa8968d967664c8bb0e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50668997"
---
# <a name="changing-the-properties-of-multiple-accelerator-keys-c"></a>變更屬性的多個快速鍵 （c + +）

### <a name="to-change-the-properties-of-multiple-accelerator-keys"></a>若要變更多個快速鍵屬性

1. 開啟快速鍵對應表，其在圖示上按兩下[資源檢視](../windows/resource-view-window.md)。

   > [!NOTE]
   > 如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。

2. 選取您想要變更按住的快速鍵**Ctrl**當您按一下每個索引鍵。

3. 移至[屬性 視窗](/visualstudio/ide/reference/properties-window)和您想要選取加速器，若要共用的所有值的型別。

   > [!NOTE]
   > 每個修飾詞值會顯示為布林值屬性中**屬性**視窗。 如果您變更[修飾詞](../windows/accelerator-modifier-property.md)中的值**屬性** 視窗中，快速鍵對應表視為新的修飾詞的補充先前有任何修飾詞。 因為這個緣故，如果您設定任何修飾詞的值，您必須設定它們，以確保每個加速器共用相同的所有**修飾詞**設定。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[編輯快速鍵對應表](../windows/editing-accelerator-tables.md)<br/>
[快速鍵編輯器](../windows/accelerator-editor.md)