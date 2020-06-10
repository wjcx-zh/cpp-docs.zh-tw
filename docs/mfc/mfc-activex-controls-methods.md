---
title: MFC ActiveX 控制項：方法
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], methods
ms.assetid: e20271de-6ffa-4ba0-848b-bafe6c9e510c
ms.openlocfilehash: 9f9ec06852ed0376583363df7649331a0be02105
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621242"
---
# <a name="mfc-activex-controls-methods"></a>MFC ActiveX 控制項：方法

ActiveX 控制項會引發事件，以便在本身與其控制項容器之間進行通訊。 容器也可以透過方法和屬性，與控制項通訊。 方法也稱為函數。

方法和屬性提供匯出的介面供其他應用程式使用，例如 Automation 用戶端和 ActiveX 控制項容器。 如需 ActiveX 控制項屬性的詳細資訊，請參閱[MFC Activex 控制項：屬性](mfc-activex-controls-properties.md)一文。

方法與 c + + 類別成員函式的用法和用途類似。 您的控制項可以執行兩種類型的方法： stock 和 custom。 就像 stock 事件一樣，內建方法是[COleControl](reference/colecontrol-class.md)提供實作為的方法。 如需有關內建方法的詳細資訊，請參閱[MFC ActiveX 控制項：加入](mfc-activex-controls-adding-stock-methods.md)內建方法一文。 開發人員所定義的自訂方法，可允許控制項的其他自訂。 如需詳細資訊，請參閱[MFC ActiveX 控制項：加入自訂方法](mfc-activex-controls-adding-custom-methods.md)一文。

MFC 程式庫（MFC）會執行一種機制，讓您的控制項支援內建和自訂的方法。 第一個部分是類別 `COleControl` 。 衍生自 `CWnd` ， `COleControl` 成員函式支援所有 ActiveX 控制項通用的內建方法。 這項機制的第二個部分是分派對應。 分派對應類似于訊息對應;不過，分派對應會將虛擬成員函式對應至 IDispatch 識別碼，而不是將函數對應至 Windows 訊息識別碼。

若要讓控制項正確支援各種方法，其類別必須宣告分派對應。 這是由位於控制項類別標頭中的下列程式程式碼所完成（。H）檔案：

[!code-cpp[NVC_MFC_AxUI#13](codesnippet/cpp/mfc-activex-controls-methods_1.h)]

分派對應的主要目的是要在外部呼叫端（例如容器）所使用的方法名稱與用來執行方法之控制項類別的成員函式之間建立關聯性。 在宣告分派對應之後，必須在控制項的實作為（中定義）。CPP）檔案。 下列幾行程式碼會定義分派對應：

[!code-cpp[NVC_MFC_AxUI#14](codesnippet/cpp/mfc-activex-controls-methods_2.cpp)]
[!code-cpp[NVC_MFC_AxUI#15](codesnippet/cpp/mfc-activex-controls-methods_3.cpp)]

如果您使用[MFC ActiveX Control Wizard](reference/mfc-activex-control-wizard.md)來建立專案，這些行會自動新增。 如果未使用 MFC ActiveX 控制項 Wizard，您必須手動加入這些行。

下列文章會詳細討論方法：

- [MFC ActiveX 控制項：新增內建方法](mfc-activex-controls-adding-stock-methods.md)

- [MFC ActiveX 控制項：新增自訂方法](mfc-activex-controls-adding-custom-methods.md)

- [MFC ActiveX 控制項：從方法傳回錯誤碼](mfc-activex-controls-returning-error-codes-from-a-method.md)

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項](mfc-activex-controls.md)
