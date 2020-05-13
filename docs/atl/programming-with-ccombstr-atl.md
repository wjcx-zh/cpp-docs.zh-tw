---
title: 使用 CComBSTR 進行程式設計 (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- CComBSTR class, programming with
- Unicode, using CComBSTR [ATL]
ms.assetid: d3bd0851-d132-4be9-9c4c-6ccba17acb2b
ms.openlocfilehash: 020c2d18c721e658d15bb1451039154ae50b99f6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321786"
---
# <a name="programming-with-ccombstr-atl"></a>使用 CComBSTR 進行程式設計 (ATL)

ATL 類[CComBSTR](../atl/reference/ccombstr-class.md)提供圍繞 BSTR 資料類型的包裝器。 雖然`CComBSTR`是一個有用的工具,但有幾個情況需要謹慎。

- [轉換問題](#programmingwithccombstr_conversionissues)

- [範圍問題](#programmingwithccombstr_scopeissues)

- [明確釋放 CComBSTR 物件](#programmingwithccombstr_explicitlyfreeing)

- [在循環中使用 CComBSTR 物件](#programmingwithccombstr_usingloops)

- [記憶體洩漏問題](#programmingwithccombstr_memoryleaks)

## <a name="conversion-issues"></a><a name="programmingwithccombstr_conversionissues"></a>轉換問題

儘管多`CComBSTR`種方法將自動將 ANSI 字串參數轉換為 Unicode,但這些方法將始終返回 Unicode 格式字串。 要將輸出字串轉換回 ANSI,請使用 ATL 轉換類。 有關 ATL 轉換類別資訊,請參閱[ATL 和 MFC 字串轉換巨集](reference/string-conversion-macros.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#114](../atl/codesnippet/cpp/programming-with-ccombstr-atl_1.cpp)]

如果使用字串文本來修改`CComBSTR`物件,請使用寬字串。 這將減少不必要的轉換。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#115](../atl/codesnippet/cpp/programming-with-ccombstr-atl_2.cpp)]

## <a name="scope-issues"></a><a name="programmingwithccombstr_scopeissues"></a>範圍問題

與任何表現良好的類一樣,當它超出範圍`CComBSTR`時,它將釋放其資源。 如果函數返回指向字串的`CComBSTR`指標,則可能會導致問題,因為指標將引用已釋放的記憶體。 在這些情況下,請使用方法,`Copy`如下所示。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#116](../atl/codesnippet/cpp/programming-with-ccombstr-atl_3.cpp)]

## <a name="explicitly-freeing-the-ccombstr-object"></a><a name="programmingwithccombstr_explicitlyfreeing"></a>明確釋放 CComBSTR 物件

在物件超出作用域之前,`CComBSTR`可以顯式釋放物件中包含的字串。 如果釋放字串,則`CComBSTR`該物件無效。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#117](../atl/codesnippet/cpp/programming-with-ccombstr-atl_4.cpp)]

## <a name="using-ccombstr-objects-in-loops"></a><a name="programmingwithccombstr_usingloops"></a>在循環中使用 CComBSTR 物件

由於`CComBSTR`類分配緩衝區以執行某些操作(`+=`如 運算符`Append`或方法),因此不建議在緊密迴圈內執行字串操作。 在這些情況下,`CStringT`提供更好的性能。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#118](../atl/codesnippet/cpp/programming-with-ccombstr-atl_5.cpp)]

## <a name="memory-leak-issues"></a><a name="programmingwithccombstr_memoryleaks"></a>記憶體洩漏問題

將初始`CComBSTR`化的位址作為 **[out]** 參數傳遞給函數會導致記憶體洩漏。

在下面的示例中,當函數`"Initialized"``MyGoodFunction`替換字串時,分配給保存字串的字串將洩露。

[!code-cpp[NVC_ATL_Utilities#119](../atl/codesnippet/cpp/programming-with-ccombstr-atl_6.cpp)]

為避免洩漏,請在現有`Empty``CComBSTR`物件上調用方法,然後再將地址作為 **[out]** 參數傳遞。

請注意,如果函數的參數**為 [在,出],** 則相同的代碼不會導致洩漏。

## <a name="see-also"></a>另請參閱

[概念](../atl/active-template-library-atl-concepts.md)<br/>
[CStringT 類別](../atl-mfc-shared/reference/cstringt-class.md)<br/>
[wstring](../standard-library/basic-string-class.md)<br/>
[字串轉換巨集](../atl/reference/string-conversion-macros.md)
