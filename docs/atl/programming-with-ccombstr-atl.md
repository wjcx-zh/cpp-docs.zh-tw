---
title: 使用 ccombstr 進行 (ATL) 程式設計 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CComBSTR class, programming with
- Unicode, using CComBSTR [ATL]
ms.assetid: d3bd0851-d132-4be9-9c4c-6ccba17acb2b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b957cca4ff1af93d3f62ab0bf667462c91b81bba
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32357853"
---
# <a name="programming-with-ccombstr-atl"></a>使用 CComBSTR 進行程式設計 (ATL)
ATL 類別[CComBSTR](../atl/reference/ccombstr-class.md)提供周圍的包裝函式`BSTR`資料型別。 雖然`CComBSTR`是有用的工具，在幾種情況需要注意。  
  
-   [轉換的問題](#programmingwithccombstr_conversionissues)  
  
-   [範圍的問題](#programmingwithccombstr_scopeissues)  
  
-   [明確地釋放 CComBSTR 物件](#programmingwithccombstr_explicitlyfreeing)  
  
-   [在迴圈中使用 CComBSTR 物件](#programmingwithccombstr_usingloops)  
  
-   [記憶體遺漏的問題](#programmingwithccombstr_memoryleaks)  
  
##  <a name="programmingwithccombstr_conversionissues"></a> 轉換的問題  
 雖然數個`CComBSTR`方法會自動將 ANSI 字串引數轉換成 Unicode，方法一律會傳回 Unicode 格式字串。 若要將輸出字串轉換回 ANSI，使用 ATL 轉換類別。 如需 ATL 轉換類別的詳細資訊，請參閱[ATL 和 MFC 字串轉換巨集](reference/string-conversion-macros.md)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities#114](../atl/codesnippet/cpp/programming-with-ccombstr-atl_1.cpp)]  
  
 如果您用來修改字串常值`CComBSTR`物件，請使用寬字元字串。 這樣會減少不必要的轉換。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities#115](../atl/codesnippet/cpp/programming-with-ccombstr-atl_2.cpp)]  
  
##  <a name="programmingwithccombstr_scopeissues"></a> 範圍的問題  
 如同任何運作良好的類別，`CComBSTR`超出範圍時便會釋放其資源。 如果函式的指標`CComBSTR`字串，這可能會造成問題，因為指標會參考已經釋放的記憶體。 在這些情況下，使用**複製**方法，如下所示。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities#116](../atl/codesnippet/cpp/programming-with-ccombstr-atl_3.cpp)]  
  
##  <a name="programmingwithccombstr_explicitlyfreeing"></a> 明確地釋放 CComBSTR 物件  
 您可明確地釋放字串中包含`CComBSTR`之前在物件超出範圍的物件。 如果會釋放字串，`CComBSTR`物件無效。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities#117](../atl/codesnippet/cpp/programming-with-ccombstr-atl_4.cpp)]  
  
##  <a name="programmingwithccombstr_usingloops"></a> 在迴圈中使用 CComBSTR 物件  
 做為`CComBSTR`類別配置一個緩衝區來執行某些作業，例如`+=`運算子或**附加**方法，不建議您執行在緊密迴圈內的字串操作。 在這些情況下，`CStringT`提供更佳的效能。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities#118](../atl/codesnippet/cpp/programming-with-ccombstr-atl_5.cpp)]  
  
##  <a name="programmingwithccombstr_memoryleaks"></a> 記憶體遺漏的問題  
 傳遞的位址初始化`CComBSTR`做 **[out]** 參數會使記憶體流失。  
  
 在下列範例中，字串配置來容納字串`"Initialized"`遭到洩露時函式`MyGoodFunction`取代的字串。  
  
 [!code-cpp[NVC_ATL_Utilities#119](../atl/codesnippet/cpp/programming-with-ccombstr-atl_6.cpp)]  
  
 若要避免流失，請呼叫**空**方法對現有`CComBSTR`物件傳遞為位址之前 **[out]** 參數。  
  
 請注意，相同的程式碼可能不會造成流失函式的參數是否 **[中，out]**。  
  
## <a name="see-also"></a>另請參閱  
 [概念](../atl/active-template-library-atl-concepts.md)   
 [CStringT 類別](../atl-mfc-shared/reference/cstringt-class.md)   
 [wstring](../standard-library/basic-string-class.md)   
 [字串轉換巨集](../atl/reference/string-conversion-macros.md)

