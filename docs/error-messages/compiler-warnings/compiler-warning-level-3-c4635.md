---
title: 編譯器警告 （層級 3） C4635 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4635
dev_langs:
- C++
helpviewer_keywords:
- C4635
ms.assetid: b2ba90de-c093-4a76-8076-b65878467574
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7651012d4c48d420734a9c6ec2ff051718f82007
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46038109"
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

請注意，這個範例的輸出顯示： **結束標記 'member' 與起始標籤 'summary' 不對稱。**

此範例的問題是結束標記\<摘要 > 格式不正確，而且編譯器無法辨認為\<摘要 > 結束標記。  \<成員 > 標記內嵌於.xdc 檔案中的每個 /doc 編譯中的編譯器。  因此，此處的問題在於結束標記\</member >，不符合先前的開始標記編譯器處理 (\<摘要 >。