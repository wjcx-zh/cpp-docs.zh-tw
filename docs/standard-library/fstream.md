---
title: '&lt;fstream&gt;'
ms.date: 11/04/2016
f1_keywords:
- <fstream>
helpviewer_keywords:
- fstream header
ms.assetid: 660de351-0489-41df-b239-40e0cdcab46b
ms.openlocfilehash: 46f65f746179740f2d67dd1ada2f96ab3fb6aaf6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87203230"
---
# <a name="ltfstreamgt"></a>&lt;fstream&gt;

定義可對外部檔案中儲存之序列的 iostreams 作業提供支援的數個類別。

## <a name="syntax"></a>語法

```cpp
#include <fstream>
```

### <a name="typedefs"></a>Typedefs

|類型名稱|說明|
|-|-|
|[filebuf](../standard-library/fstream-typedefs.md#filebuf)|`basic_filebuf`範本參數上特製化的類型 **`char`** 。|
|[a m](../standard-library/fstream-typedefs.md#fstream)|`basic_fstream`範本參數上特製化的類型 **`char`** 。|
|[ifstream](../standard-library/fstream-typedefs.md#ifstream)|`basic_ifstream`範本參數上特製化的類型 **`char`** 。|
|[ofstream](../standard-library/fstream-typedefs.md#ofstream)|`basic_ofstream`範本參數上特製化的類型 **`char`** 。|
|[wfstream](../standard-library/fstream-typedefs.md#wfstream)|`basic_fstream`範本參數上特製化的類型 **`wchar_t`** 。|
|[wifstream](../standard-library/fstream-typedefs.md#wifstream)|`basic_ifstream`範本參數上特製化的類型 **`wchar_t`** 。|
|[wofstream](../standard-library/fstream-typedefs.md#wofstream)|`basic_ofstream`範本參數上特製化的類型 **`wchar_t`** 。|
|[wfilebuf](../standard-library/fstream-typedefs.md#wfilebuf)|`basic_filebuf`範本參數上特製化的類型 **`wchar_t`** 。|

### <a name="classes"></a>類別

|類別|說明|
|-|-|
|[basic_filebuf](../standard-library/basic-filebuf-class.md)|類別樣板描述的資料流程緩衝區，可控制類型的專案 `Elem` （其字元特性是由類別所決定 `Tr` ），與外部檔案中儲存的專案序列之間的傳輸。|
|[basic_fstream](../standard-library/basic-fstream-class.md)|類別樣板描述的物件可控制如何使用類別 basic_filebuf 的資料流程緩衝區來插入和解壓縮專案和編碼物件[basic_filebuf](../standard-library/basic-filebuf-class.md) \<**Elem**, **Tr**> ， `Elem` 其字元特性是由類別所決定 `Tr` 。|
|[basic_ifstream](../standard-library/basic-ifstream-class.md)|類別樣板所描述的物件，可控制從[basic_filebuf](../standard-library/basic-filebuf-class.md)類別的資料流程緩衝區（具有類型的元素）中的專案和編碼物件的提取， \<**Elem**, **Tr**> `Elem` 其字元特性是由類別所決定 `Tr` 。|
|[basic_ofstream](../standard-library/basic-ofstream-class.md)|類別樣板描述的物件可控制如何將元素和編碼物件插入至類別 basic_filebuf 的資料流程緩衝區[basic_filebuf](../standard-library/basic-filebuf-class.md) \<**Elem**, **Tr**> ，其中包含類型的元素 `Elem` ，其字元特性是由類別所決定 `Tr` 。|

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)\
[C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream 程式設計](../standard-library/iostream-programming.md)\
[iostreams 慣例](../standard-library/iostreams-conventions.md)
