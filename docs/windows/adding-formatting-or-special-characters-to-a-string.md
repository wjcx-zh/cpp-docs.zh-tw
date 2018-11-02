---
title: 將格式或特殊字元新增至字串資源 （c + +）
ms.date: 11/04/2016
helpviewer_keywords:
- special characters, adding to strings
- ASCII characters, adding to strings
- strings [C++], formatting
- strings [C++], special characters
ms.assetid: c40f394a-8b2c-4896-ab30-6922863ddbb5
ms.openlocfilehash: 740bf02d40dfcb236eef0dccbf55201dd79aec4c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50493843"
---
# <a name="adding-formatting-or-special-characters-to-a-string-resource-c"></a>將格式或特殊字元新增至字串資源 （c + +）

### <a name="to-add-formatting-or-special-characters-to-a-string"></a>若要為字串加入格式或特殊字元

1. 開啟字串資料表，其在圖示上按兩下[資源檢視](../windows/resource-view-window.md)。

   > [!NOTE]
   > 如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。

2. 選取您想要修改的字串。

3. 在 [[屬性] 視窗](/visualstudio/ide/reference/properties-window)，新增任何標準逸出序列的下面所列中的文字**標題** 方塊中，然後按**Enter**。

   |若要取得此|輸入這|
   |-----------------|---------------|
   |換行|\n|
   |歸位字元|\r|
   |索引標籤|\t|
   |反斜線 (\\)|\\\|
   |ASCII 字元|\ddd （八進位標記法）|
   |警示 （鈴聲）|\a|

> [!NOTE]
> **字串**編輯器不支援完整的逸出 ASCII 字元。 您只能使用以上所列。

如需將資源加入 managed 專案 （其為目標的通用語言執行平台） 的資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[逐步解說： 當地語系化 Windows Forms](/previous-versions/visualstudio/visual-studio-2010/y99d1cd3)。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[字串編輯器](../windows/string-editor.md)