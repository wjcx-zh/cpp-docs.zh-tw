---
title: '&lt;fstream&gt;'
ms.date: 11/04/2016
f1_keywords:
- <fstream>
helpviewer_keywords:
- fstream header
ms.assetid: 660de351-0489-41df-b239-40e0cdcab46b
ms.openlocfilehash: ba6a4152b8d37f5b0186f9d05c6ba850e8c2e54c
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68454025"
---
# <a name="ltfstreamgt"></a>&lt;fstream&gt;

定義可對外部檔案中儲存之序列的 iostreams 作業提供支援的數個類別。

## <a name="syntax"></a>語法

```cpp
#include <fstream>
```

### <a name="typedefs"></a>Typedefs

|類型名稱|描述|
|-|-|
|[filebuf](../standard-library/fstream-typedefs.md#filebuf)|在`basic_filebuf` **char**樣板參數上特製化的類型。|
|[fstream](../standard-library/fstream-typedefs.md#fstream)|在`basic_fstream` **char**樣板參數上特製化的類型。|
|[ifstream](../standard-library/fstream-typedefs.md#ifstream)|在`basic_ifstream` **char**樣板參數上特製化的類型。|
|[ofstream](../standard-library/fstream-typedefs.md#ofstream)|在`basic_ofstream` **char**樣板參數上特製化的類型。|
|[wfstream](../standard-library/fstream-typedefs.md#wfstream)|在`basic_fstream` **wchar_t**範本參數上特製化的類型。|
|[wifstream](../standard-library/fstream-typedefs.md#wifstream)|在`basic_ifstream` **wchar_t**範本參數上特製化的類型。|
|[wofstream](../standard-library/fstream-typedefs.md#wofstream)|在`basic_ofstream` **wchar_t**範本參數上特製化的類型。|
|[wfilebuf](../standard-library/fstream-typedefs.md#wfilebuf)|在`basic_filebuf` **wchar_t**範本參數上特製化的類型。|

### <a name="classes"></a>類別

|類別|描述|
|-|-|
|[basic_filebuf](../standard-library/basic-filebuf-class.md)|範本類別描述資料流緩衝區，其控制類型 `Elem` 的項目 (其字元特性由類別 `Tr` 所決定)，與外部檔案中儲存的項目序列之間的往來傳輸。|
|[basic_fstream](../standard-library/basic-fstream-class.md)|此樣板類別所描述的物件, 可控制如何使用類別[basic_filebuf](../standard-library/basic-filebuf-class.md) \< **Elem**, `Elem` **Tr**> 的資料流程緩衝區來插入和解壓縮專案和編碼物件, 其型別為的元素字元特性是由類別`Tr`所決定。|
|[basic_ifstream](../standard-library/basic-ifstream-class.md)|此樣板類別所描述的物件, 可控制從[basic_filebuf](../standard-library/basic-filebuf-class.md) \< **Elem**, **Tr**> 類別的資料流程緩衝區中的專案和編碼物件的提取, 其中`Elem`包含類型的元素, 其字元特性是由類別`Tr`所決定。|
|[basic_ofstream](../standard-library/basic-ofstream-class.md)|此樣板類別所描述的物件, 可控制如何將元素和編碼物件插入至[basic_filebuf](../standard-library/basic-filebuf-class.md) \< **Elem**, **Tr**> 類別的資料流程緩衝區, 其中包含`Elem`類型的元素, 其字元特性為是由類別`Tr`所決定。|

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)\
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream 程式設計](../standard-library/iostream-programming.md)\
[iostream 慣例](../standard-library/iostreams-conventions.md)
