---
title: MFC ActiveX 控制項：方法
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], methods
ms.assetid: e20271de-6ffa-4ba0-848b-bafe6c9e510c
ms.openlocfilehash: 71c4cdd5ea07b3468b7878a221129a0de5eb4974
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57268404"
---
# <a name="mfc-activex-controls-methods"></a>MFC ActiveX 控制項：方法

ActiveX 控制項就會引發事件本身和其控制項容器之間進行通訊。 容器也可以進行通訊與控制項透過方法和屬性。 方法也會呼叫函式。

方法和屬性提供用於匯出的介面，由其他應用程式，例如自動化用戶端和 ActiveX 控制項容器。 如需有關 ActiveX 控制項屬性的詳細資訊，請參閱文章[MFC ActiveX 控制項：屬性](../mfc/mfc-activex-controls-properties.md)。

方法是在使用中且用途的 c + + 類別的成員函式類似。 有兩種方法可以實作您的控制項類型： 內建和自訂。 類似於內建事件、 內建方法，是那些方法[COleControl](../mfc/reference/colecontrol-class.md)提供實作。 如需有關內建方法的詳細資訊，請參閱文章[MFC ActiveX 控制項：加入內建方法](../mfc/mfc-activex-controls-adding-stock-methods.md)。 開發人員所定義的自訂方法可讓控制項的其他自訂。 如需詳細資訊，請參閱文章[MFC ActiveX 控制項：新增自訂方法](../mfc/mfc-activex-controls-adding-custom-methods.md)。

Microsoft Foundation Class 程式庫 (MFC) 會實作一種機制，可讓您的控制項支援內建及自訂的方法。 第一個部分是類別`COleControl`。 衍生自`CWnd`，`COleControl`成員函式支援通用於所有的 ActiveX 控制項的內建方法。 這項機制的第二個部分是分派對應。 分派對應是類似的訊息對應;不過，而不是將函式對應至 Windows 訊息識別碼，分派對應會對應至 IDispatch 識別碼的虛擬成員函式。

控制項，無法正確支援各種方法，它的類別必須宣告分派對應。 這可以藉由下列程式碼位於控制項類別標頭檔 (。H） 檔案：

[!code-cpp[NVC_MFC_AxUI#13](../mfc/codesnippet/cpp/mfc-activex-controls-methods_1.h)]

分派對應的主要目的是類別的建立外部呼叫者 （例如容器） 和控制項成員函式的實作方法所使用的方法名稱之間的關聯性。 在宣告的分派對應之後，它必須定義在控制項的實作 (。CPP) 檔案。 下列程式碼定義分派對應：

[!code-cpp[NVC_MFC_AxUI#14](../mfc/codesnippet/cpp/mfc-activex-controls-methods_2.cpp)]
[!code-cpp[NVC_MFC_AxUI#15](../mfc/codesnippet/cpp/mfc-activex-controls-methods_3.cpp)]

如果您使用[MFC ActiveX 控制項精靈](../mfc/reference/mfc-activex-control-wizard.md)來建立專案時，這幾行已自動新增。 如果未使用 MFC ActiveX 控制項精靈，您必須手動加入這些行。

下列文章將討論詳細的方法：

- [MFC ActiveX 控制項：加入內建方法](../mfc/mfc-activex-controls-adding-stock-methods.md)

- [MFC ActiveX 控制項：新增自訂方法](../mfc/mfc-activex-controls-adding-custom-methods.md)

- [MFC ActiveX 控制項：從方法傳回錯誤碼](../mfc/mfc-activex-controls-returning-error-codes-from-a-method.md)

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)
