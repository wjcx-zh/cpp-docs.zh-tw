---
title: 變更 [標題] 屬性的多個字串資源 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- String editor [C++], changing properties of multiple strings
- string tables [C++], changing caption of multiple strings
ms.assetid: 82ac4389-fd9c-4794-a18f-c6bf5b253bd7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fe08462c95750f483cdec5650fccb1c199505ee1
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/11/2018
ms.locfileid: "49082393"
---
# <a name="changing-the-caption-property-of-multiple-string-resources-c"></a>變更 [標題] 屬性的多個字串資源 （c + +）

下列程序會示範如何將多個字串的標題屬性變更。

### <a name="to-change-the-caption-property-of-multiple-strings"></a>若要變更多個字串的標題屬性

1. 開啟字串資料表，其在圖示上按兩下[資源檢視](../windows/resource-view-window.md)。

   > [!NOTE]
   > 如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。

2. 選取您想要變更按住的字串**Ctrl**當您按一下每個索引鍵。

3. 在 [[屬性] 視窗](/visualstudio/ide/reference/properties-window)，輸入您想要變更屬性的新值。

4. 按 **Enter** 鍵。

如需將資源加入 managed 專案 （其為目標的通用語言執行平台） 的資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[逐步解說： 當地語系化 Windows Forms](/previous-versions/visualstudio/visual-studio-2010/y99d1cd3)。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[字串編輯器](../windows/string-editor.md)  