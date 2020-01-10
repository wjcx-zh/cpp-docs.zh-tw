---
title: 編譯器警告 (層級 3) C4635
ms.date: 11/04/2016
f1_keywords:
- C4635
helpviewer_keywords:
- C4635
ms.assetid: b2ba90de-c093-4a76-8076-b65878467574
ms.openlocfilehash: fd3bf6c1b14c6dae8e2fa95a54e2d4fbc4f295c5
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991846"
---
# <a name="compiler-warning-level-3-c4635"></a>編譯器警告 (層級 3) C4635

XML 文件註解目標: XML 格式錯誤: 原因

編譯器發現 XML 標記有一些問題。  請修正問題並重新編譯。

下列範例會產生 C4635：

```cpp
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

這個範例的問題是，\<摘要 > 的結束標記格式不正確，而且編譯器無法將它辨識為 \<摘要 > 結束標記。  \<成員 > 標記是由編譯器在每個/doc 編譯中內嵌于 .xdc 檔案中。  因此，此處的問題在於，\</member > 的結束標記不符合編譯器處理的上一個開始標記（\<摘要 >。
