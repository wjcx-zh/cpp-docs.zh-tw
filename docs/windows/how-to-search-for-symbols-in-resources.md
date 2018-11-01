---
title: 如何： 在資源 （c + +） 中的搜尋符號
ms.date: 11/04/2016
helpviewer_keywords:
- symbols [C++], finding
- resources [C++], searching for symbols
ms.assetid: 6efef8e8-d0d4-4c49-b895-314974e7791a
ms.openlocfilehash: b289fa1c2e5e5e1997c5024b21cae3d7a22b2b8f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50655970"
---
# <a name="how-to-search-for-symbols-in-resources-c"></a>如何： 在資源 （c + +） 中的搜尋符號

### <a name="to-find-symbols-in-resources"></a>若要尋找資源中的符號

1. 從**編輯**功能表上，選擇**尋找符號**。

2. 在 [[尋找符號] 對話方塊中](/visualstudio/ide/go-to)，請在**尋找目標**方塊中，從下拉式清單中選取先前的搜尋字串或輸入您想要尋找 （例如，ID_ACCEL1） 的快速鍵。

   > [!TIP]
   > 若要使用[規則運算式](/visualstudio/ide/using-regular-expressions-in-visual-studio)進行搜尋，您必須使用[檔案中尋找命令](/visualstudio/ide/reference/find-command)從**編輯**功能表，而不是**尋找符號**命令。 若要啟用的規則運算式，您必須擁有**使用： 規則運算式**中所選取的核取方塊[尋找對話方塊](/visualstudio/ide/finding-and-replacing-text)。 然後您可以按一下右邊的向右箭號按鈕**Find What**方塊，以顯示規則搜尋運算式的清單。 當您從這份清單中選取運算式時，它會替換成索引中的搜尋文字**Find What**  方塊中。

3. 選取任一**尋找**選項。

4. 按一下 **尋找下一個**。

   > [!NOTE]
   > 您無法在字串、快速鍵或二進位資源中搜尋符號。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[符號：資源識別項](../windows/symbols-resource-identifiers.md)<br/>
[資源檔](../windows/resource-files-visual-studio.md)<br/>
[資源編輯器](../windows/resource-editors.md)