---
title: HOW TO：自訂快速存取工具列
ms.date: 09/07/2019
helpviewer_keywords:
- quick access toolbar [MFC], customization
ms.assetid: 2554099b-0c89-4605-9249-31bf9cbcefe0
ms.openlocfilehash: 8b2eb6f7c80c77f69e2bbb65b7bb31a385014c8c
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907786"
---
# <a name="how-to-customize-the-quick-access-toolbar"></a>作法：自訂快速存取工具列

快速存取工具列 (QAT) 是包含一組命令的可自訂工具列，命令是顯示在 [應用程式] 按鈕旁或類別索引標籤下。 下圖將顯示一般的快速存取工具列。

![MFC 功能區快速存取工具列](../mfc/media/quick_access_toolbar.png "MFC 功能區快速存取工具列")

若要自訂快速存取工具列，請在 [**屬性**] 視窗中開啟它，修改其命令，然後預覽功能區控制項。

### <a name="to-open-the-quick-access-toolbar-in-the-properties-window"></a>在屬性視窗中開啟快速存取工具列

1. 在 Visual Studio 的 [ **View** ] 功能表上，按一下 [**資源檢視**]。

1. 在**資源檢視**中，按兩下功能區資源，將它顯示在設計介面上。

1. 在設計介面上，以滑鼠右鍵按一下 [快速存取工具列] 功能表，然後按一下 [**屬性**]。

## <a name="quick-access-toolbar-properties"></a>快速存取工具列屬性

下表定義快速存取工具列的屬性。

|屬性|定義|
|--------------|----------------|
|QAT 位置|當應用程式啟動時，指定快速存取工具列的位置。 位置可以是功能區控制項的**上方**或**下方**。|
|QAT 項目|指定快速存取工具列可用的命令。|

#### <a name="to-add-or-remove-commands-on-the-quick-access-toolbar"></a>在快速存取工具列上新增或移除命令

1. 在 [**屬性**] 視窗中，按一下 [ **QAT 專案**]，然後按一下省略號按鈕 **（...）** 。

1. 在 [ **QAT 專案編輯器**] 對話方塊中，使用 [**新增**] 和 [**移除**] 按鈕來修改快速存取工具列上的命令清單。

1. 如果您想要命令顯示在快速存取工具列和快速存取工具列功能表上，請選取命令旁的方塊。 如果您想要命令只出現在功能表中，請清除方塊。

## <a name="previewing-the-ribbon"></a>預覽功能區

快速存取工具列命令未出現在設計介面上。 若要檢視它們，您必須預覽功能區或執行應用程式。

#### <a name="to-preview-the-ribbon-control"></a>預覽功能區控制項

- 在**功能區編輯器工具列**上，按一下 [**測試] 功能區**。

## <a name="see-also"></a>另請參閱

[功能區設計工具 (MFC)](../mfc/ribbon-designer-mfc.md)
