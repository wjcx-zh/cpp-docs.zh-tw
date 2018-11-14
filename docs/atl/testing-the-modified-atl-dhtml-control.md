---
title: 測試已修改的 ATL DHTML 控制項
ms.date: 11/06/2018
helpviewer_keywords:
- HTML controls, testing
- testing controls
- DHTML controls, testing
ms.assetid: 42316118-9433-410f-9d8a-0efcc1eff824
ms.openlocfilehash: 99f55807a7da647af0961f73c600ae0e31166cdc
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2018
ms.locfileid: "51330966"
---
# <a name="testing-the-modified-atl-dhtml-control"></a>測試已修改的 ATL DHTML 控制項

試試看您新的控制項，以查看其如何運作。

## <a name="to-build-and-test-the-modified-control"></a>若要建置並測試修改過的控制項

1. 重建專案並開啟它**測試容器**。 請參閱[以測試容器測試屬性和事件](../mfc/testing-properties-and-events-with-test-container.md)如需如何存取**Test Container**。

   調整大小以顯示所有您加入的按鈕控制項。

1. 檢查您所更改的 HTML 插入兩個按鈕。 每個按鈕與您在所識別的標籤[修改 ATL DHTML 控制項](../atl/modifying-the-atl-dhtml-control.md):**重新整理**並**HelloHTML**。

1. 測試新的兩個按鈕，以查看其運作方式。

現在測試不屬於 UI 的方法。

1. 反白顯示控制項，以便啟動框線。

1. 在 **控制**功能表上，選擇**叫用方法**。

   標示為清單中的方法**方法名稱**容器可以呼叫的方法：`MethodInvoked`和`GoToURL`。 所有其他的方法是由 UI 控制。

1. 選取的方法來叫用，並選擇**Invoke**以顯示方法的訊息方塊，或瀏覽至`www.microsoft.com`。

1. 在 **叫用方法**對話方塊方塊中，選擇**關閉**。

若要深入了解各種項目和 ATL DHTML 控制項所組成的檔案，請參閱[識別 DHTML 控制項專案的項目](../atl/identifying-the-elements-of-the-dhtml-control-project.md)。

## <a name="see-also"></a>另請參閱

[DHTML 控制項的支援](../atl/atl-support-for-dhtml-controls.md)
