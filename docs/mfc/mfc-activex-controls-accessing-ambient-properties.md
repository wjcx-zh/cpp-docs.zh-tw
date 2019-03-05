---
title: MFC ActiveX 控制項：存取環境屬性
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], accessing ambient properties
- properties [MFC], accessing ambient
ms.assetid: fdc9db29-e6b0-45d2-a879-8bd60e2058a7
ms.openlocfilehash: 585ec8720a654bbcb728330d70ddb914f2543e41
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57305220"
---
# <a name="mfc-activex-controls-accessing-ambient-properties"></a>MFC ActiveX 控制項：存取環境屬性

這篇文章討論如何 ActiveX 控制項可以存取其控制項容器的環境屬性。

控制項可以存取容器的環境屬性，以取得其容器的相關資訊。 這些屬性會公開視覺特性，例如容器的背景色彩，使用容器和作業的特性，例如容器是否目前在使用者模式或設計工具模式中的目前字型。 控制項可以使用自訂其外觀和行為，以在其中內嵌的特定容器的環境屬性。 不過，控制項應該永遠不會假設其容器將會支援任何特定的環境屬性中。 事實上，某些容器可能不完全支援任何環境的屬性。 如果沒有使用環境的屬性，控制項應該假設合理的預設值。

若要存取環境屬性，請呼叫[COleControl::GetAmbientProperty](../mfc/reference/colecontrol-class.md#getambientproperty)。 此函式第一個參數 (olectl 預期環境屬性分派識別碼。H 定義一組標準的環境屬性的分派 Id）。

參數的`GetAmbientProperty`函式會分派識別碼，而預期的屬性型別，以及記憶體的指標，指出 variant 標記應該在其中傳回的值。 將這個指標所參考的資料型別會因 variant 的標記。 此函數會傳回**真**如果容器支援的屬性，否則會傳回**FALSE**。

下列程式碼範例會取得值的環境的屬性，叫做 「 使用者 」 模式。 如果屬性不支援的容器，預設值是 **，則為 TRUE**假設：

[!code-cpp[NVC_MFC_AxUI#30](../mfc/codesnippet/cpp/mfc-activex-controls-accessing-ambient-properties_1.cpp)]

為了方便起見，`COleControl`提供存取許多常用的環境屬性，並傳回適當的預設值，無法使用屬性時的協助程式函式。 這些 helper 函式如下所示：

- [COleControl::AmbientBackColor](../mfc/reference/colecontrol-class.md#ambientbackcolor)

- [AmbientDisplayName](../mfc/reference/colecontrol-class.md#ambientdisplayname)

- [AmbientFont](../mfc/reference/colecontrol-class.md#ambientfont)

    > [!NOTE]
    >  呼叫端必須呼叫`Release( )`上傳回的字型。

- [AmbientForeColor](../mfc/reference/colecontrol-class.md#ambientforecolor)

- [AmbientLocaleID](../mfc/reference/colecontrol-class.md#ambientlocaleid)

- [AmbientScaleUnits](../mfc/reference/colecontrol-class.md#ambientscaleunits)

- [AmbientTextAlign](../mfc/reference/colecontrol-class.md#ambienttextalign)

- [AmbientUserMode](../mfc/reference/colecontrol-class.md#ambientusermode)

- [AmbientUIDead](../mfc/reference/colecontrol-class.md#ambientuidead)

- [AmbientShowHatching](../mfc/reference/colecontrol-class.md#ambientshowhatching)

- [AmbientShowGrabHandles](../mfc/reference/colecontrol-class.md#ambientshowgrabhandles)

如果環境屬性的值變更 （透過某些動作的容器）、`OnAmbientPropertyChanged`呼叫成員函式的控制項。 覆寫此成員函式，來處理這類通知。 參數`OnAmbientPropertyChanged`是受影響的環境屬性的分派識別碼。 這個分派識別碼的值可能是 DISPID_UNKNOWN，表示一或多個環境的屬性已變更，但無法使用哪些屬性已受到影響的資訊。

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)
