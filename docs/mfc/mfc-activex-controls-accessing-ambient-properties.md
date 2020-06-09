---
title: MFC ActiveX 控制項：存取環境屬性
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], accessing ambient properties
- properties [MFC], accessing ambient
ms.assetid: fdc9db29-e6b0-45d2-a879-8bd60e2058a7
ms.openlocfilehash: e5c78c9943f8baeadcc1198ee8c96f2023ac0215
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625438"
---
# <a name="mfc-activex-controls-accessing-ambient-properties"></a>MFC ActiveX 控制項：存取環境屬性

本文會討論 ActiveX 控制項如何存取其控制項容器的環境屬性。

控制項可以藉由存取容器的環境屬性來取得其容器的相關資訊。 這些屬性會公開視覺特性，例如容器的背景色彩、容器所使用的目前字型，以及作業特性（例如容器目前處於使用者模式或設計工具模式）。 控制項可以使用環境屬性，針對其內嵌所在的特定容器，量身打造其外觀和行為。 不過，控制項絕對不應假設其容器會支援任何特定的環境屬性。 事實上，有些容器可能完全不支援任何環境屬性。 在沒有環境屬性的情況下，控制項應假設有合理的預設值。

若要存取環境屬性，請呼叫[COleControl：： GetAmbientProperty](reference/colecontrol-class.md#getambientproperty)。 此函式需要環境屬性的分派識別碼做為第一個參數（檔案 OLECTL。H 定義一組標準環境屬性的分派識別碼）。

函式的參數 `GetAmbientProperty` 是分派識別碼、表示預期屬性類型的 variant 標記，以及應該傳回值之記憶體的指標。 這個指標所參考的資料類型會根據 variant 標記而有所不同。 如果容器支援屬性，則函數會傳回**TRUE** ，否則會傳回**FALSE**。

下列程式碼範例會取得名為 "UserMode" 之環境屬性的值。 如果容器不支援此屬性，則會假設為**TRUE**的預設值：

[!code-cpp[NVC_MFC_AxUI#30](codesnippet/cpp/mfc-activex-controls-accessing-ambient-properties_1.cpp)]

為了方便起見， `COleControl` 提供 helper 函式來存取許多常用的環境屬性，並在屬性無法使用時傳回適當的預設值。 這些 helper 函式如下所示：

- [COleControl：： AmbientBackColor](reference/colecontrol-class.md#ambientbackcolor)

- [AmbientDisplayName](reference/colecontrol-class.md#ambientdisplayname)

- [AmbientFont](reference/colecontrol-class.md#ambientfont)

    > [!NOTE]
    >  呼叫端必須 `Release( )` 在傳回的字型上呼叫。

- [AmbientForeColor](reference/colecontrol-class.md#ambientforecolor)

- [AmbientLocaleID](reference/colecontrol-class.md#ambientlocaleid)

- [AmbientScaleUnits](reference/colecontrol-class.md#ambientscaleunits)

- [AmbientTextAlign](reference/colecontrol-class.md#ambienttextalign)

- [AmbientUserMode](reference/colecontrol-class.md#ambientusermode)

- [AmbientUIDead](reference/colecontrol-class.md#ambientuidead)

- [AmbientShowHatching](reference/colecontrol-class.md#ambientshowhatching)

- [AmbientShowGrabHandles](reference/colecontrol-class.md#ambientshowgrabhandles)

如果環境屬性的值變更（透過容器的某些動作），則 `OnAmbientPropertyChanged` 會呼叫控制項的成員函式。 覆寫此成員函式以處理這類通知。 的參數 `OnAmbientPropertyChanged` 是受影響環境屬性的分派識別碼。 此分派識別碼的值可能會 DISPID_UNKNOWN，這表示一個或多個環境屬性已變更，但無法使用哪些屬性受影響的相關資訊。

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項](mfc-activex-controls.md)
