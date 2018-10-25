---
title: 編輯版本資訊資源 （c + +） 內的字串 |Microsoft Docs
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
- version information resources [C++]
- resources [C++], editing version information
ms.assetid: d3a7d4e4-7d31-47c2-902c-f50b8404ba4f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5a456c745a11fa4250ad731f00556b211ad21b8f
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50061699"
---
# <a name="editing-a-string-in-a-version-information-resource-c"></a>編輯版本資訊資源 （c + +） 內的字串

### <a name="to-edit-a-string-in-a-version-information-resource"></a>編輯版本資訊資源內的字串

1. 按一下並選取項目，然後再按一次開始編輯。 進行變更直接在**版本資訊**資料表或在[屬性 視窗](/visualstudio/ide/reference/properties-window)。 您所做的變更會反映在這兩個位置。

   > [!NOTE]
   > 編輯時`FILEFLAGS`中的索引鍵**版本資訊**編輯器中，您會發現您無法設定**偵錯**，**私用組建**，或**特殊建置**屬性 (在**屬性**視窗).rc 檔：

   - **版本資訊**編輯器組**偵錯**屬性`#ifdef`中的資源指令碼中，根據`_DEBUG`組建旗標。

   - 如果`Private Build`機碼具有**值**中設定**版本資訊**資料表中，對應**私用組建**屬性 (在**屬性**  視窗) 的`FILEFLAGS`索引鍵會是 **，則為 True**。 如果 [值]  是空的，則該屬性為 **False**。 同樣地， **Special Build**機碼 (在**版本資訊**資料表) 會繫結至**Special Build**屬性`FILEFLAGS`索引鍵。

您可以按一下 [機碼] 或 [值] 欄位標題，來排序字串區塊的資訊順序。 這些標題會自動依照選取的順序重新排列資訊。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[版本資訊編輯器](../windows/version-information-editor.md)<br/>
[版本資訊 (Windows)](https://msdn.microsoft.com/library/windows/desktop/ms646981.aspx)