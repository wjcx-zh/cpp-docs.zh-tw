---
title: 建構輸入資料流物件
ms.date: 11/04/2016
helpviewer_keywords:
- input stream objects
ms.assetid: ab94866e-6ffe-4f15-b4db-0bd23e636075
ms.openlocfilehash: f281741979680fc03d3f96d2dbfbac6e1feefdea
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228306"
---
# <a name="constructing-input-stream-objects"></a>建構輸入資料流物件

如果您只使用 `cin` 物件，就不需要建構輸入資料流。 如果您使用下列項目，就必須建構輸入資料流︰

- [輸入檔案資料流程的函式](#vclrfinputfilestreamconstructorsanchor8)

- [輸入字串資料流程函數](#vclrfinputstringstreamconstructorsanchor9)

## <a name="input-file-stream-constructors"></a><a name="vclrfinputfilestreamconstructorsanchor8"></a> 輸入檔案資料流建構函式

下列兩種方式可用來建立輸入檔案資料流：

- 使用引數的函式 **`void`** ，然後呼叫成員函式 `open` ：

   ```cpp
   ifstream myFile; // On the stack
   myFile.open("filename");

   ifstream* pmyFile = new ifstream; // On the heap
   pmyFile->open("filename");
   ```

- 在建構函式引動過程中，指定檔案名稱和模式旗標，以在建構程序期間開啟檔案：

   ```cpp
   ifstream myFile("filename");
   ```

## <a name="input-string-stream-constructors"></a><a name="vclrfinputstringstreamconstructorsanchor9"></a> 輸入字串資料流建構函式

輸入字串資料流建構函式需要您已預先配置並初始化的儲存體位址：

```cpp
string s("123.45");

double amt;
istringstream myString(s);

//istringstream myString("123.45") also works
myString>> amt; // amt contains 123.45
```

## <a name="see-also"></a>另請參閱

[輸入資料流程](../standard-library/input-streams.md)
