---
title: assert 函式所列印的診斷 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 78b64200-520d-40da-9a61-71553f411d4f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ac5473a2dd592bbd9af2f65044d3d7d97515dc37
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46103382"
---
# <a name="diagnostic-printed-by-the-assert-function"></a>assert 函式所列印的診斷

**ANSI 4.2** 由 **assert** 函式所列印的診斷，以及該函式的終止行為

**assert** 函式會列印診斷訊息，並在運算式為 false (0) 時，呼叫 **abort** 常式。 診斷資訊的格式如下

> **判斷提示失敗**: <em>expression</em>**，檔案** <em>filename</em>**，行號** *linenumber*

其中，*filename* 是來源檔案的名稱，而 *linenumber* 是來源檔案中發生失敗的判斷提示行號。 如果 *expression*為 true (非零)，則不會採取任何動作。

## <a name="see-also"></a>請參閱

[程式庫函式](../c-language/library-functions.md)