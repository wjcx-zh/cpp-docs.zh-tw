---
title: MFC ActiveX 控制項：屬性
ms.date: 11/04/2016
helpviewer_keywords:
- properties [MFC], ActiveX controls
- MFC ActiveX controls [MFC], properties
- properties [MFC]
ms.assetid: b678a53c-0d9e-476f-8aa0-23b80baaba46
ms.openlocfilehash: 5e01854e7ae7acdc33275351d0d26a76dfeabc9b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62324320"
---
# <a name="mfc-activex-controls-properties"></a>MFC ActiveX 控制項：屬性

ActiveX 控制項就會引發其控制項容器與通訊的事件。 容器，用以方法和屬性的控制項進行通訊。 方法與屬性類似，在使用中且用途，分別是，成員函式和成員變數的C++類別。 屬性會公開任何容器的資料成員的 ActiveX 控制項。 屬性包含 ActiveX 控制項，例如自動化用戶端和 ActiveX 控制項容器應用程式提供的介面。

屬性也稱為屬性。

如需有關 ActiveX 控制項方法的詳細資訊，請參閱文章[MFC ActiveX 控制項：方法](../mfc/mfc-activex-controls-methods.md)。

內建和自訂方法和屬性，可以實作 ActiveX 控制項。 類別`COleControl`提供內建屬性的實作。 (如內建屬性完整清單，請參閱文章[MFC ActiveX 控制項：加入內建屬性](../mfc/mfc-activex-controls-adding-stock-properties.md)。)開發人員所定義的自訂屬性會加入 ActiveX 控制項中的特製化的功能。 如需詳細資訊，請參閱[MFC ActiveX 控制項：將自訂屬性新增](../mfc/mfc-activex-controls-adding-custom-properties.md)。

自訂和內建的屬性，例如方法，都受到包含處理屬性和方法以及現有的成員函式的分派對應機制`COleControl`類別。 此外，這些屬性可以有開發人員將額外的資訊傳遞至控制項所使用的參數。

下列文章會討論更多詳細資料中的 ActiveX 控制項屬性：

- [MFC ActiveX 控制項：加入內建屬性](../mfc/mfc-activex-controls-adding-stock-properties.md)

- [MFC ActiveX 控制項：加入自訂屬性](../mfc/mfc-activex-controls-adding-custom-properties.md)

- [MFC ActiveX 控制項：進階的屬性實作](../mfc/mfc-activex-controls-advanced-property-implementation.md)

- [MFC ActiveX 控制項：存取環境屬性](../mfc/mfc-activex-controls-accessing-ambient-properties.md)

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)
