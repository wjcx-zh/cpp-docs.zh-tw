---
title: MFC ActiveX 控制項：屬性
ms.date: 11/04/2016
helpviewer_keywords:
- properties [MFC], ActiveX controls
- MFC ActiveX controls [MFC], properties
- properties [MFC]
ms.assetid: b678a53c-0d9e-476f-8aa0-23b80baaba46
ms.openlocfilehash: c7ed0fddea660409f5089159b71d39a29b01d538
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618177"
---
# <a name="mfc-activex-controls-properties"></a>MFC ActiveX 控制項：屬性

ActiveX 控制項會引發事件，以與其控制項容器通訊。 傳回的容器會使用方法和屬性來與控制項通訊。 方法和屬性在使用和用途上分別類似于 c + + 類別的成員函式和成員變數。 屬性是 ActiveX 控制項的資料成員，會向任何容器公開。 屬性會為包含 ActiveX 控制項的應用程式（例如自動化用戶端和 ActiveX 控制項容器）提供介面。

屬性也稱為屬性。

如需 ActiveX 控制項方法的詳細資訊，請參閱[MFC Activex 控制項：方法](mfc-activex-controls-methods.md)一文。

ActiveX 控制項可以同時執行內建和自訂方法和屬性。 類別 `COleControl` 提供內建屬性的執行。 （如需庫存屬性的完整清單，請參閱[MFC ActiveX 控制項：加入](mfc-activex-controls-adding-stock-properties.md)內建屬性一文。）自訂屬性（由開發人員定義）會將特殊功能加入至 ActiveX 控制項。 如需詳細資訊，請參閱[MFC ActiveX 控制項：加入自訂屬性](mfc-activex-controls-adding-custom-properties.md)。

自訂和內建屬性（如方法）受到由處理屬性和方法的分派對應，以及類別的現有成員函式所支援的機制 `COleControl` 。 此外，這些屬性可以有開發人員用來傳遞額外資訊給控制項的參數。

下列文章會更詳細地討論 ActiveX 控制項屬性：

- [MFC ActiveX 控制項：新增內建屬性](mfc-activex-controls-adding-stock-properties.md)

- [MFC ActiveX 控制項：新增自訂屬性](mfc-activex-controls-adding-custom-properties.md)

- [MFC ActiveX 控制項：進階屬性實作](mfc-activex-controls-advanced-property-implementation.md)

- [MFC ActiveX 控制項：存取環境屬性](mfc-activex-controls-accessing-ambient-properties.md)

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項](mfc-activex-controls.md)
