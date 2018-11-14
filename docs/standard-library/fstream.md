---
title: '&lt;fstream&gt;'
ms.date: 11/04/2016
f1_keywords:
- <fstream>
helpviewer_keywords:
- fstream header
ms.assetid: 660de351-0489-41df-b239-40e0cdcab46b
ms.openlocfilehash: 20efdc755b7f706fc6ee962daa32bd352df39d45
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2018
ms.locfileid: "51522892"
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
|[filebuf](../standard-library/fstream-typedefs.md#filebuf)|型別`basic_filebuf`特殊化**char**範本參數。|
|[fstream](../standard-library/fstream-typedefs.md#fstream)|型別`basic_fstream`特殊化**char**範本參數。|
|[ifstream](../standard-library/fstream-typedefs.md#ifstream)|型別`basic_ifstream`特殊化**char**範本參數。|
|[ofstream](../standard-library/fstream-typedefs.md#ofstream)|型別`basic_ofstream`特殊化**char**範本參數。|
|[wfstream](../standard-library/fstream-typedefs.md#wfstream)|型別`basic_fstream`特殊化**wchar_t**範本參數。|
|[wifstream](../standard-library/fstream-typedefs.md#wifstream)|型別`basic_ifstream`特殊化**wchar_t**範本參數。|
|[wofstream](../standard-library/fstream-typedefs.md#wofstream)|型別`basic_ofstream`特殊化**wchar_t**範本參數。|
|[wfilebuf](../standard-library/fstream-typedefs.md#wfilebuf)|型別`basic_filebuf`特殊化**wchar_t**範本參數。|

### <a name="classes"></a>類別

|類別|描述|
|-|-|
|[basic_filebuf](../standard-library/basic-filebuf-class.md)|範本類別描述資料流緩衝區，其控制類型 `Elem` 的項目 (其字元特性由類別 `Tr` 所決定)，與外部檔案中儲存的項目序列之間的往來傳輸。|
|[basic_fstream](../standard-library/basic-fstream-class.md)|此範本類別描述的物件可控制插入及擷取元素和編碼的物件使用類別的資料流緩衝區[basic_filebuf](../standard-library/basic-filebuf-class.md)\<**Elem**， **Tr**>，類型的項目`Elem`，其字元特性由類別`Tr`。|
|[basic_ifstream](../standard-library/basic-ifstream-class.md)|此範本類別描述的物件可控制擷取元素和編碼的物件類別的資料流緩衝區[basic_filebuf](../standard-library/basic-filebuf-class.md)\<**Elem**， **Tr**>，類型的項目`Elem`，其字元特性由類別`Tr`。|
|[basic_ofstream](../standard-library/basic-ofstream-class.md)|此範本類別描述的物件可控制插入的項目和編碼的物件的類別的資料流緩衝區[basic_filebuf](../standard-library/basic-filebuf-class.md)\<**Elem**， **Tr**>，類型的項目`Elem`，其字元特性由類別`Tr`。|

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream 程式設計](../standard-library/iostream-programming.md)<br/>
[iostream 慣例](../standard-library/iostreams-conventions.md)<br/>
