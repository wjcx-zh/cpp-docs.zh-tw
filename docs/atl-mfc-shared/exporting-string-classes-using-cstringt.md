---
title: 匯出字串類別使用 CStringT |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CStringT class, exporting strings
ms.assetid: bdfc441e-8d2a-461c-9885-46178066c09f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f2d77516ae53b0ee1c4f39e4d8f095848aa00acc
ms.sourcegitcommit: d3c41b16bf05af2149090e996d8e71cd6cd55c7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2018
ms.locfileid: "48889967"
---
# <a name="exporting-string-classes-using-cstringt"></a>使用 CStringT 匯出字串類別

在過去，MFC 開發人員有衍生自`CString`特製化他們自己的字串類別。 在 Microsoft Visual c + +.NET (MFC 8.0) [CString](../atl-mfc-shared/using-cstring.md)類別已取代的範本類別，稱為[CStringT](../atl-mfc-shared/reference/cstringt-class.md)。 這提供數個優點：

- 它允許 MFC`CString`類別用於 ATL 專案而不連結在較大的 MFC 靜態程式庫或 DLL 中。

- 與新`CStringT`樣板類別，您可以自訂`CString`使用指定的字元特性，類似於 c + + 標準程式庫中範本的範本參數的行為。

- 當您將自己的字串類別匯出從 DLL，使用`CStringT`，編譯器也會自動匯出`CString`基底類別。 由於`CString`本身是樣板類別，它可能會具現化編譯器使用時，除非編譯器知道，`CString`從 DLL 匯入。 如果您有移轉專案從 Visual c + + 6.0 到 Visual c + +.NET，您可能會看到如多重定義的連結器的符號錯誤`CString`因為衝突而`CString`匯入從 DLL，並在本機上具現化的版本。 若要這樣做的正確方式如下所述。

下列案例會導致連結器產生的符號錯誤多次定義的類別。 假設您要匯出`CString`-衍生的類別 (`CMyString`) 從 MFC 擴充 DLL:

[!code-cpp[NVC_MFC_DLL#6](../atl-mfc-shared/codesnippet/cpp/exporting-string-classes-using-cstringt_1.cpp)]

取用者程式碼會使用混合`CString`和`CMyString`。 「 MyString.h"不包含在先行編譯標頭，與一些使用方式`CString`沒有`CMyString`可見。

假設您使用`CString`和`CMyString`個別原始程式檔，Source1.cpp 和 Source2.cpp 中的類別。 在 Source1.cpp，您可以使用`CMyString`和 #include MyString.h。 在 Source2.cpp，您可以使用`CString`，但卻不符 #include MyString.h。 在此情況下，連結器會產生負面反應相關`CStringT`multiply 所定義。 這所致`CString`正在同時從匯出的 DLL 匯入`CMyString`，並透過編譯器具現化，在本機`CStringT`範本。

若要解決此問題，請執行下列作業：

匯出`CStringA`和`CStringW`（和必要的基底類別） 從 MFC90。DLL。 包含 MFC 的專案一律會使用 MFC DLL 匯出`CStringA`和`CStringW`，在舊版的 MFC 實作中。

然後使用下列方法建立可匯出的衍生的類別`CStringT`範本，做為`CStringT_Exported`低於，例如：

[!code-cpp[NVC_MFC_DLL#7](../atl-mfc-shared/codesnippet/cpp/exporting-string-classes-using-cstringt_2.cpp)]

在 AfxStr.h，取代先前`CString`， `CStringA`，和`CStringW`typedef，如下所示：

[!code-cpp[NVC_MFC_DLL#8](../atl-mfc-shared/codesnippet/cpp/exporting-string-classes-using-cstringt_3.cpp)]

有數個需要注意的事項：

- 您不應該匯出`CStringT`本身因為這會造成匯出特製化的僅限 ATL 專案`CStringT`類別。

- 使用可匯出衍生類別`CStringT`最小化 需要重新實作`CStringT`功能。 額外的程式碼僅限於轉送以建構函式`CStringT`基底類別。

- `CString``CStringA`，並`CStringW`才會標記`__declspec(dllexport/dllimport)`當您使用 MFC 建置時共用的 DLL。 如果連結的 MFC 靜態程式庫，您應該不這些類別標示為匯出;否則，內部使用`CString`， `CStringA`，和`CStringW`內使用者 Dll 會將標示`CString`一併匯出。

## <a name="related-topics"></a>相關主題

[CStringT 類別](../atl-mfc-shared/reference/cstringt-class.md)

## <a name="see-also"></a>另請參閱

[使用 CStringT](../atl-mfc-shared/using-cstringt.md)<br/>
[使用 CString](../atl-mfc-shared/using-cstring.md)

