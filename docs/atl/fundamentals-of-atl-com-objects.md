---
title: ATL COM 物件的基本概念
ms.date: 11/19/2018
helpviewer_keywords:
- COM, and ATL
- ATL, COM
- ATL COM objects
- COM objects, ATL
ms.assetid: 0f9c9d98-cc28-45da-89ac-dc94cee422fe
ms.openlocfilehash: ec83539b2d7101c534bbc1df33577df422e76152
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492372"
---
# <a name="fundamentals-of-atl-com-objects"></a>ATL COM 物件的基本概念

下圖描述用來定義 ATL COM 物件的類別和介面之間的關聯性。

![ATL 結構](../atl/media/vc307y1.gif "ATL 結構")

> [!NOTE]
>  `CComObject`此圖表顯示衍生自`CComPolyObject` `CComAggObject` `CYourClass` , 而包含`CYourClass`做為成員變數。

有三種方式可定義 ATL COM 物件。 標準選項是使用衍生自`CComObject` `CYourClass`的類別。 第二個選項是使用`CComAggObject`類別來建立匯總物件。 第三個選項是使用`CComPolyObject`類別。 `CComPolyObject`做為混合式: 它可以做為`CComObject`類別或`CComAggObject`類別, 視其第一次建立的方式而定。 如需如何使用類別的`CComPolyObject`詳細資訊, 請參閱[CComPolyObject 類別](../atl/reference/ccompolyobject-class.md)。

當您使用標準 ATL COM 時, 您會使用兩個物件: 外部物件和內建物件。 外部用戶端會透過外部物件中定義的包裝函式來存取內建物件的功能。 外部物件的類型`CComObject`為。

當您使用匯總物件時, 外部物件不會提供內建物件功能的包裝函式。 相反地, 外部物件會提供外部用戶端直接存取的指標。 在此案例中, 外部物件的類型`CComAggObject`為。 內建物件是外部物件的成員變數, 而且屬於型`CYourClass`別。

因為用戶端不需要經過外部物件來與內建物件互動, 所以匯總物件通常會更有效率。 此外, 如果用戶端可以直接取得匯總物件的介面, 則外部物件不需要知道匯總物件的功能。 不過, 並非所有的物件都可以匯總。 針對要匯總的物件, 必須將它設計為要考慮匯總。

ATL 會以兩個階段來實行[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) :

- [CComObject](../atl/reference/ccomobject-class.md)、 [CComAggObject](../atl/reference/ccomaggobject-class.md)或[CComPolyObject](../atl/reference/ccompolyobject-class.md) `IUnknown`會執行方法。

- [CComObjectRoot](../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md)會管理的參考計數和`IUnknown`外部指標。

ATL COM 物件的其他層面會由其他類別處理:

- [CComCoClass](../atl/reference/ccomcoclass-class.md)會定義物件的預設 Class Factory 和匯總模型。

- [IDispatchImpl](../atl/reference/idispatchimpl-class.md)提供物件上任何雙重介面`IDispatch Interface`部分的預設執行。

- [Isupporterrorinfoimpl 當成基類會](../atl/reference/isupporterrorinfoimpl-class.md)執行介面,以確保正確地傳播呼叫鏈的錯誤資訊。`ISupportErrorInfo`

## <a name="in-this-section"></a>本節內容

[實作 CComObjectRootEx](../atl/implementing-ccomobjectrootex.md)<br/>
顯示用於執行`CComObjectRootEx`的範例 COM 對應專案。

[實作 CComObject、CComAggObject 和 CComPolyObject](../atl/implementing-ccomobject-ccomaggobject-and-ccompolyobject.md)<br/>
討論**DECLARE_\*_AGGREGATABLE**宏如何`CComObject`影響、 `CComAggObject`和`CComPolyObject`的使用。

[支援 IDispatch 和 IErrorInfo](../atl/supporting-idispatch-and-ierrorinfo.md)<br/>
列出要用來支援`IDispatch`和`IErrorInfo`介面的 ATL 實作為類別。

[支援 IDispEventImpl](../atl/supporting-idispeventimpl.md)<br/>
討論為您的類別執行連接點的步驟。

[變更預設 Class Factory 和彙總模型](../atl/changing-the-default-class-factory-and-aggregation-model.md)<br/>
顯示要用來變更預設 Class Factory 和匯總模型的宏。

[建立彙總物件](../atl/creating-an-aggregated-object.md)<br/>
列出建立匯總物件的步驟。

## <a name="related-sections"></a>相關章節

[建立 ATL 專案](../atl/reference/creating-an-atl-project.md)<br/>
提供有關建立 ATL COM 物件的資訊。

[ATL](../atl/active-template-library-atl-concepts.md)<br/>
提供有關如何使用 Active Template Library 進行程式設計的概念性主題連結。

## <a name="see-also"></a>另請參閱

[概念](../atl/active-template-library-atl-concepts.md)
