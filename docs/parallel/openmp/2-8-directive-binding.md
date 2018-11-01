---
title: 2.8 指示詞繫結
ms.date: 11/04/2016
ms.assetid: 7bdac45e-ab55-42f0-bd47-a2e3d5bbab3e
ms.openlocfilehash: fb22d1b503303842ff73550c1c6544cae7e5f2f3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50528608"
---
# <a name="28-directive-binding"></a>2.8 指示詞繫結

動態繫結的指示詞必須遵守下列規則：

- **For**，**各節**，**單一**，**主要**，並**屏障**指示詞將繫結至動態封閉式**平行**，如果有的話，不論任何的值為何**如果**可能存在於該指示詞上的子句。 如果沒有平行區域目前正在執行中，只有主要執行緒所組成的小組所執行指示詞。

- **排序**指示詞將繫結至動態封閉**如**。

- **Atomic**指示詞會強制執行獨佔存取權，相對於**不可部分完成**所有執行緒，而不只是目前的小組中的指示詞。

- **重大**指示詞會強制執行獨佔存取權，相對於**重要**所有執行緒，而不只是目前的小組中的指示詞。

- 指示詞可以永遠不會繫結至最接近以外的任何指示詞動態封閉**平行**。