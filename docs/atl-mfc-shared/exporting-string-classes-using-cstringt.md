---
title: 匯出字串類別使用 CStringT |Microsoft 文件
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
ms.openlocfilehash: 7510b1f44f49d17211c71419f4dde5a6e6a78974
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32356392"
---
# <a name="exporting-string-classes-using-cstringt"></a>匯出使用 CStringT 的字串類別
在過去，MFC 開發人員必須衍生自`CString`他們自己的字串類別特製化。 在 Microsoft Visual c + +.NET (MFC 8.0) [CString](../atl-mfc-shared/using-cstring.md)類別已被呼叫的樣板類別[CStringT](../atl-mfc-shared/reference/cstringt-class.md)。 這會提供數個優點：  
  
-   它允許 MFC`CString`類別用於 ATL 專案而不連結更大的 MFC 靜態程式庫或 DLL 中。  
  
-   與新`CStringT`樣板類別，您可以自訂`CString`行為使用的範本參數所指定字元特性，類似於 c + + 標準程式庫中的範本。  
  
-   當您匯出您自己的字串類別使用`CStringT`，編譯器也會自動匯出`CString`基底類別。 因為`CString`本身是樣板類別，它可能會具現化編譯器使用時，除非編譯器可感知的`CString`從 DLL 匯入。 如果您已從 Visual c + + 6.0 移轉專案，Visual c + +.net，您可能會看到乘以定義的連結器的符號錯誤`CString`因為衝突而`CString`匯入從 DLL，並在本機上具現化的版本。 若要這樣做的正確方式如下所述。 如需有關此問題的詳細資訊，請參閱知識庫文件中，「 連結錯誤，當您匯入 CString 衍生類別 」 (Q309801) 在[ http://support.microsoft.com/default.aspx ](http://support.microsoft.com/default.aspx)。  
  
 下列案例會導致連結器產生的符號錯誤多次定義的類別。 假設您要匯出`CString`-衍生的類別 (`CMyString`) 從 MFC 擴充 DLL:  
  
 [!code-cpp[NVC_MFC_DLL#6](../atl-mfc-shared/codesnippet/cpp/exporting-string-classes-using-cstringt_1.cpp)]  
  
 取用者程式碼使用的混合`CString`和`CMyString`。 「 MyString.h"不包含在先行編譯標頭和的一些用法`CString`沒有`CMyString`可見。  
  
 假設您使用`CString`和`CMyString`不同原始程式檔，Source1.cpp 和 Source2.cpp 中的類別。 Source1.cpp，在您使用`CMyString`和 #include MyString.h。 Source2.cpp，在您使用`CString`，但卻沒有 #include MyString.h。 在此情況下，連結器將能投訴地`CStringT`正在定義多次。 這因為`CString`正在同時從匯出的 DLL 匯入`CMyString`，而且透過編譯器具現化，在本機`CStringT`範本。  
  
 若要解決這個問題，請執行下列各項：  
  
 匯出`CStringA`和`CStringW`（和必要的基底類別） 從 MFC90。DLL。 專案包含 MFC 一律會使用 MFC DLL 匯出`CStringA`和`CStringW`，在先前的 MFC 實作中。  
  
 然後建立可匯出的衍生的類別使用`CStringT`範本，做為`CStringT_Exported`低於，例如：  
  
 [!code-cpp[NVC_MFC_DLL#7](../atl-mfc-shared/codesnippet/cpp/exporting-string-classes-using-cstringt_2.cpp)]  
  
 在 AfxStr.h，取代先前`CString`， `CStringA`，和`CStringW`typedef，如下所示：  
  
 [!code-cpp[NVC_MFC_DLL#8](../atl-mfc-shared/codesnippet/cpp/exporting-string-classes-using-cstringt_3.cpp)]  
  
 有幾個警告：  
  
-   您不應該匯出`CStringT`本身因為這會造成匯出的特定的僅限 ATL 專案`CStringT`類別。  
  
-   使用匯出衍生自`CStringT`降到最低的不必重新實作`CStringT`功能。 額外的程式碼僅限於轉送建構函式來`CStringT`基底類別。  
  
-   `CString``CStringA`，和`CStringW`只應標記為`__declspec(dllexport/dllimport)`建立時，您使用 MFC 共用 DLL。 如果連結的 MFC 靜態程式庫，您應該會將標示這些類別為匯出。否則，內部使用`CString`， `CStringA`，和`CStringW`內使用者 Dll 會將標示為`CString`以及匯出。  
  
## <a name="related-topics"></a>相關主題  
 [CStringT 類別](../atl-mfc-shared/reference/cstringt-class.md)  
  
## <a name="see-also"></a>另請參閱  
 [使用 CStringT](../atl-mfc-shared/using-cstringt.md)   
 [使用 CString](../atl-mfc-shared/using-cstring.md)

