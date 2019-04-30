---
title: abort 函式
ms.date: 12/01/2017
helpviewer_keywords:
- abort function
ms.assetid: 3352bcc4-1a8a-4e1f-8dcc-fe30f6b50f2d
ms.openlocfilehash: 7c87cb4fe7349a0d623c765c20e7e213a8454571
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385098"
---
# <a name="abort-function"></a>abort 函式

**中止**函式，也在標準 include 檔中宣告\<stdlib.h >，結束C++程式。 之間的差異`exit`並**中止**在於`exit`可讓C++執行階段終止處理 （全域物件會呼叫解構函式），而**中止**會立即終止程式。 如需詳細資訊，請參閱 <<c0> [ 中止](../c-runtime-library/reference/abort.md)中*執行階段程式庫參考*。

## <a name="see-also"></a>另請參閱

[程式終止](../cpp/program-termination.md)