---
title: 編譯器警告 (層級 3) C4635
ms.date: 11/04/2016
f1_keywords:
- C4635
helpviewer_keywords:
- C4635
ms.assetid: b2ba90de-c093-4a76-8076-b65878467574
ms.openlocfilehash: 21873a883b19924ce3ef41511d65f8ae640875f4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401718"
---
# <a name="compiler-warning-level-3-c4635"></a>編譯器警告 (層級 3) C4635

XML 文件註解目標: XML 格式錯誤: 原因

編譯器發現 XML 標記有一些問題。  請修正問題並重新編譯。

下列範例會產生 C4635：

```
// C4635.cpp
// compile with: /doc /clr /W3 /c
/// <summary>
/// The contents of the folder have changed.
/// <summary/>   // C4635

// try the following line instead
// /// </summary>
public ref class Test {};
```

請注意，此範例的輸出顯示：**結束標記 'member' 與起始標籤 'summary' 不相符。**

此範例的問題是結束標記\<摘要 > 格式不正確，而且編譯器無法辨認為\<摘要 > 結束標記。  \<成員 > 標記內嵌於.xdc 檔案中的每個 /doc 編譯中的編譯器。  因此，此處的問題在於結束標記\</member >，不符合先前的開始標記編譯器處理 (\<摘要 >。