---
title: C++ 程式庫慣例
ms.date: 11/04/2016
helpviewer_keywords:
- C++ Standard Library, conventions
- classes [C++]
- functions [C++], library naming conventions
- naming conventions [C++], C++ Standard Library
- conventions [C++], C++ Standard Library
- function names [C++]
- coding conventions, C++ Standard Library
- naming conventions [C++], C++ library
ms.assetid: bf41b79a-2d53-4f46-8d05-779358335146
ms.openlocfilehash: f1790b75baea340d0b3ab1044290317055ac81d7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62210771"
---
# <a name="c-library-conventions"></a>C++ 程式庫慣例

C++ 程式庫遵循的慣例大致與標準 C 程式庫相同，再加上幾個此處概述的慣例。

在 C++ 程式庫中，實作宣告其類型和函式的方式具有特定層次：

- 標準 C 程式庫中的函式名稱可能會有 extern #"C++" 或 extern "C" 連結。 包含適當的標準 C 標頭，而不是宣告程式庫的實體內嵌。

- 在程式庫類別中，成員函式名稱可能具有本文件所列以外的其他函式簽章。 您可以確定此處所述的函式呼叫具有預期的行為，但是卻無法確實採用程式庫成員函式的位址， 因為類型可能跟您所預期的不同。

- 程式庫類別可能具有未記載的 (非虛擬) 基底類別。 記載為衍生自其他類別的類別，實際上可能是透過其他未記載的類別而衍生自該類別。

- 定義為某個整數類型之同義字的類型，有可能與數個不同整數類型之一相同。

- 位元遮罩類型可以實作為整數類型或列舉。 您可以在任一情況下，執行相同位元遮罩類型值的位元運算 (例如 `AND` 和`OR`)。 `A` 和 `B` 元素的位元遮罩類型是非零值，因此 `A` & `B` 為零。

- 如果程式庫函式不含例外狀況規格，即可傳回任意例外狀況，除非其定義已明確限制這種可能性。

另一方面，仍有下列限制：

- 標準 C 程式庫不會使用遮罩巨集。 只會保留簽章的特定函式，而不是函式本身的名稱。

- 在類別之外的程式庫函式名稱不會有其他未記載的函式簽章。 您可以確實採用其位址。

- 描述為虛擬的基底類別和成員函式確實為虛擬，而描述為非虛擬的函式亦確實為非虛擬。

- C++ 程式庫所定義的兩種類型都不同 (除非這份文件明確表明其他情況)。

- 程式庫提供的函式 (包括可取代函式的預設版本) 最多可以擲回任何例外狀況規格中所列的這些例外狀況。 程式庫所提供的任何解構函式都不能擲回例外狀況。 標準 C 程式庫中的函式可能會傳播例外狀況 (例如當 `qsort` 呼叫會擲回例外狀況的比較函式時)，但卻不會擲回例外狀況。

## <a name="see-also"></a>另請參閱

[C++ 標準程式庫概觀](../standard-library/cpp-standard-library-overview.md)<br/>
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
