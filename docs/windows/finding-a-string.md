---
title: 尋找字串資源 （c + +） |Microsoft Docs
ms.date: 11/04/2016
f1_keywords:
- vc.editors.string
helpviewer_keywords:
- strings [C++], searching
- strings [C++]
ms.assetid: c2497173-f356-4f77-97d6-f0ac41782510
ms.openlocfilehash: 0e6d8ac8027028377e903a9e0a3c89238a9862a2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50585917"
---
# <a name="finding-a-string-resource-c"></a>尋找字串資源 （c + +）

您可以搜尋一或多個字串在字串資料表中，並使用[規則運算式](/visualstudio/ide/using-regular-expressions-in-visual-studio)具有**檔案中尋找**命令 (**編輯**功能表) 來尋找所有執行個體的字串符合模式。

### <a name="to-find-a-string-in-the-string-table"></a>字串資料表中尋找字串

1. 開啟字串資料表，其在圖示上按兩下[資源檢視](../windows/resource-view-window.md)。

   > [!NOTE]
   > 如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。

2. 在上**編輯**功能表上，按一下**尋找和取代**，然後選擇**尋找**。

3. 在  **Find What**方塊中，從下拉式清單中選取先前的搜尋字串或輸入您想要尋找的字串的標題文字 或 資源識別碼。

4. 選取任一**尋找**選項。

5. 按一下 **尋找下一個**。

   > [!TIP]
   > 若要搜尋檔案時，請使用規則運算式，使用**檔案中尋找**命令。 輸入的規則運算式比對模式，或按一下右邊的按鈕**Find What**方塊，以顯示規則搜尋運算式的清單。 當您從這份清單中選取運算式時，它會替換成索引中的搜尋文字**Find What**  方塊中。 如果您使用規則運算式，請務必**使用： 規則運算式**選取核取方塊。

如需將資源加入 managed 專案 （其為目標的通用語言執行平台） 的資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[逐步解說： 當地語系化 Windows Forms](/previous-versions/visualstudio/visual-studio-2010/y99d1cd3)。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[字串編輯器](../windows/string-editor.md)