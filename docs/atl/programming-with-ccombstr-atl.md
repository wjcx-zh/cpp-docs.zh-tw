---
title: 使用 ccombstr 進行 (ATL) 程式設計 |Microsoft Docs
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
ms.openlocfilehash: e0cae1e2f05484aeccd76e987c2d63c41aec30f6
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/05/2018
ms.locfileid: "37848433"
---
# <a name="programming-with-ccombstr-atl"></a>使用 CComBSTR 進行程式設計 (ATL)
ATL 類別[CComBSTR](../atl/reference/ccombstr-class.md) BSTR 資料型別一個包裝函式。 雖然`CComBSTR`是有用的工具，有幾種情況需要注意。  
  
-   [轉換的問題](#programmingwithccombstr_conversionissues)  
  
-   [範圍問題](#programmingwithccombstr_scopeissues)  
  
-   [明確釋放 CComBSTR 物件](#programmingwithccombstr_explicitlyfreeing)  
  
-   [在迴圈中使用 CComBSTR 物件](#programmingwithccombstr_usingloops)  
  
-   [記憶體遺漏的問題](#programmingwithccombstr_memoryleaks)  
  
##  <a name="programmingwithccombstr_conversionissues"></a> 轉換的問題  
 雖然數個`CComBSTR`方法會自動將 ANSI 字串引數轉換成 Unicode，方法一律會傳回 Unicode 格式字串。 若要將輸出字串轉換回 ANSI，使用 ATL 轉換類別。 如需有關 ATL 轉換類別的詳細資訊，請參閱[ATL 和 MFC 字串轉換巨集](reference/string-conversion-macros.md)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities#114](../atl/codesnippet/cpp/programming-with-ccombstr-atl_1.cpp)]  
  
 如果您使用字串常值來修改`CComBSTR`物件，請使用寬字元字串。 這會減少不必要的轉換。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities#115](../atl/codesnippet/cpp/programming-with-ccombstr-atl_2.cpp)]  
  
##  <a name="programmingwithccombstr_scopeissues"></a> 範圍問題  
 如同任何行為良好的類別，`CComBSTR`它超出範圍時，會釋放其資源。 如果函式傳回的指標`CComBSTR`字串，這可能會造成問題，因為指標會參考已經釋放的記憶體。 在這些情況下，使用`Copy`方法，如下所示。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities#116](../atl/codesnippet/cpp/programming-with-ccombstr-atl_3.cpp)]  
  
##  <a name="programmingwithccombstr_explicitlyfreeing"></a> 明確釋放 CComBSTR 物件  
 您可明確釋放出中所包含的字串`CComBSTR`物件，才能在物件超出範圍。 如果會釋放字串，`CComBSTR`物件無效。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities#117](../atl/codesnippet/cpp/programming-with-ccombstr-atl_4.cpp)]  
  
##  <a name="programmingwithccombstr_usingloops"></a> 在迴圈中使用 CComBSTR 物件  
 作為`CComBSTR`類別會配置來執行某些作業，例如緩衝區`+=`運算子或`Append`方法，不建議您執行在緊密迴圈內的字串操作。 在這些情況下，`CStringT`提供較佳的效能。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities#118](../atl/codesnippet/cpp/programming-with-ccombstr-atl_5.cpp)]  
  
##  <a name="programmingwithccombstr_memoryleaks"></a> 記憶體遺漏的問題  
 傳遞的位址初始化`CComBSTR`做為函式 **[out]** 參數會使記憶體流失。  
  
 在下列範例中，字串配置來保留字串`"Initialized"`遭到洩露時函式`MyGoodFunction`會取代字串。  
  
 [!code-cpp[NVC_ATL_Utilities#119](../atl/codesnippet/cpp/programming-with-ccombstr-atl_6.cpp)]  
  
 若要避免外洩，呼叫`Empty`方法現有`CComBSTR`物件傳遞為位址之前 **[out]** 參數。  
  
 請注意，相同的程式碼可能不會造成流失函式的參數是否 **[在中，out]**。  
  
## <a name="see-also"></a>另請參閱  
 [概念](../atl/active-template-library-atl-concepts.md)   
 [CStringT 類別](../atl-mfc-shared/reference/cstringt-class.md)   
 [wstring](../standard-library/basic-string-class.md)   
 [字串轉換巨集](../atl/reference/string-conversion-macros.md)

