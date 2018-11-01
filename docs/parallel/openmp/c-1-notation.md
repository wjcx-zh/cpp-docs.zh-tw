---
title: C.1 標記法
ms.date: 11/04/2016
ms.assetid: a23b2631-8096-4bf3-ac23-ba4f4bd7a52a
ms.openlocfilehash: 593450b6dd7dcb30adbf8546ad96ff716c6fbc1c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50473979"
---
# <a name="c1-notation"></a>C.1 標記法

文法規則包含非-終端機中，名稱後面接著冒號，後面接著取代替代項目不同行上。

語法的運算式詞彙<sub>opt</sub>指出一詞是選擇性內取代。

語法的運算式*詞彙*<sub>optseq</sub>相當於*詞彙 seq*<sub>選擇</sub>與下列其他規則：

*詞彙 seq* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*詞彙*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*詞彙 seq* *詞彙*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*詞彙 seq* **，** *詞彙*