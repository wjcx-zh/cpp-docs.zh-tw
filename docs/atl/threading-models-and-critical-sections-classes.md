---
title: 執行緒模型和關鍵區段類別 (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- ATL, critical sections
- ATL, multithreading
- threading [ATL], models
- critical sections
ms.assetid: 759f05ef-6285-4be6-a2cc-78572dd75146
ms.openlocfilehash: 98db15a1fee2637b9493b538468fa9446015404f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62196151"
---
# <a name="threading-models-and-critical-sections-classes"></a>執行緒模型和關鍵區段類別

下列類別定義的執行緒模型和關鍵區段：

- [CAtlAutoThreadModule](../atl/reference/catlautothreadmodule-class.md)實作在執行緒集區的 apartment model COM 伺服器。

- [CAtlAutoThreadModuleT](../atl/reference/catlautothreadmodulet-class.md)提供方法來實作在執行緒集區的 apartment model COM 伺服器。

- [CComMultiThreadModel](../atl/reference/ccommultithreadmodel-class.md)遞增和遞減變數提供具備執行緒安全的方法。 提供重要的區段。

- [CComMultiThreadModelNoCS](../atl/reference/ccommultithreadmodelnocs-class.md)遞增和遞減變數提供具備執行緒安全的方法。 不會提供重要的區段。

- [CComSingleThreadModel](../atl/reference/ccomsinglethreadmodel-class.md)提供方法，來遞增及遞減變數。 不會提供重要的區段。

- [CComObjectThreadModel](../atl/reference/atl-typedefs.md#ccomobjectthreadmodel)決定單一物件類別的適當執行緒模型類別。

- [CComGlobalsThreadModel](../atl/reference/atl-typedefs.md#ccomglobalsthreadmodel)決定適當的執行緒模型類別，為全球可用的物件。

- [CComAutoCriticalSection](../atl/reference/ccomautocriticalsection-class.md)包含取得和釋放重要區段的方法。 自動初始化重要區段。

- [CComCriticalSection](../atl/reference/ccomcriticalsection-class.md)包含取得和釋放重要區段的方法。 重要區段必須先明確初始化。

- [CComFakeCriticalSection](../atl/reference/ccomfakecriticalsection-class.md)鏡像中的方法`CComCriticalSection`而不需提供重要的區段。 中的方法`CComFakeCriticalSection`不執行任何動作。

- [CRTThreadTraits](../atl/reference/crtthreadtraits-class.md)提供 CRT 執行緒建立函式。 如果執行緒會使用 CRT 函式，請使用這個類別。

- [Win32ThreadTraits](../atl/reference/win32threadtraits-class.md)提供 Windows 執行緒建立函式。 如果執行緒不會使用 CRT 函式，請使用這個類別。

## <a name="see-also"></a>另請參閱

[類別概觀](../atl/atl-class-overview.md)
