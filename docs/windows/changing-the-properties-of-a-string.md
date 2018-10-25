---
title: 變更屬性的字串資源 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- resource identifiers, string properties
- string tables [C++], changing strings
- strings [C++], properties
ms.assetid: 0a220434-f444-4405-9a64-d28d6b965687
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a873776db6381a78b99e0323e669235b7863ea04
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50067640"
---
# <a name="changing-the-properties-of-a-string-resource-c"></a>變更屬性的字串資源 （c + +）

### <a name="to-change-a-string-or-its-identifier"></a>若要變更字串或其識別碼

1. 開啟字串資料表，其在圖示上按兩下[資源檢視](../windows/resource-view-window.md)。

   > [!NOTE]
   > 如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。

2. 選取您想要編輯，然後按兩下的字串**識別碼**，**值**，或**標題**資料行。 現在您可以：

   - 選取 **識別碼**從**ID 下拉式**清單中或類型`ID`直接就地。

   - 輸入在不同的數字**值**資料行。

   - 輸入中的編輯**標題**資料行。

        > [!NOTE]
        >  您也可以編輯中的字串屬性[屬性 視窗](/visualstudio/ide/reference/properties-window)。

如需將資源加入 managed 專案 （其為目標的通用語言執行平台） 的資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[逐步解說： 當地語系化 Windows Forms](/previous-versions/visualstudio/visual-studio-2010/y99d1cd3)。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[字串編輯器](../windows/string-editor.md)