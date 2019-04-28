---
title: 建構輸出資料流物件
ms.date: 11/04/2016
helpviewer_keywords:
- output stream objects
ms.assetid: 93c8eab6-610c-4f48-b76d-1d960cac7641
ms.openlocfilehash: 7da7d9dd0fae3ce3fa21ecd774f88643dca49c26
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62211997"
---
# <a name="constructing-output-stream-objects"></a>建構輸出資料流物件

如果您只使用預先定義的 `cout`、`cerr` 或 `clog` 物件，就不需要建構輸出資料流。 您必須使用下列建構函式：

- [輸出檔案資料流建構函式](#vclrfoutputfilestreamconstructorsanchor1)

- [輸出字串資料流建構函式](#vclrfoutputstringstreamconstructorsanchor2)

## <a name="vclrfoutputfilestreamconstructorsanchor1"></a> 輸出檔案資料流建構函式

您可以使用下列兩種方式之一來建構輸出檔案資料流：

- 使用預設建構函式，然後呼叫 `open` 成員函式。

   ```cpp
   ofstream myFile; // Static or on the stack
   myFile.open("filename");

   ofstream* pmyFile = new ofstream; // On the heap
   pmyFile->open("filename");
   ```

- 在建構函式呼叫中，指定檔案名稱和模式旗標。

   ```cpp
   ofstream myFile("filename", ios_base::out);
   ```

## <a name="vclrfoutputstringstreamconstructorsanchor2"></a> 輸出字串資料流建構函式

若要建構輸出字串資料流，您可以透過下列方式使用 `ostringstream`：

```cpp
using namespace std;
// ...
ostringstream myString;
myString << "this is a test" << ends;

string sp = myString.str(); // Obtain string
cout << sp << endl;
```

`ends` 操作工具即會將必要的終止 null 字元新增至字串。

## <a name="see-also"></a>另請參閱

[輸出資料流](../standard-library/output-streams.md)<br/>
