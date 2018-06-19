---
title: 建構輸出資料流物件 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- output stream objects
ms.assetid: 93c8eab6-610c-4f48-b76d-1d960cac7641
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ff3c924327c11d00dd9137a91ebd19ef7bdc9eaa
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33850064"
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
