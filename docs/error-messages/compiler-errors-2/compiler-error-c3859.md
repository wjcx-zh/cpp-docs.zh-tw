---
title: 編譯器錯誤 C3859
ms.date: 03/08/2019
f1_keywords:
- C3859
helpviewer_keywords:
- C3859
ms.assetid: 40e93b25-4393-4467-90de-035434a665c7
ms.openlocfilehash: 9b20224207ba797c6ee93c06404e4d90c3d02525
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391877"
---
# <a name="compiler-error-c3859"></a>編譯器錯誤 C3859

> 超出; PCH 的虛擬記憶體範圍請重新編譯的命令列選項 '-Zm*值*' 或更新版本

虛擬記憶體配置的先行編譯標頭是編譯器正在嘗試放入其中的資料量太小。 在 Visual Studio 2015 中，啟動 **/Zm**使用時，才重要建議`#pragma hdrstop`指示詞。 在其他情況下，它是假的錯誤，指出 Windows 虛擬記憶體不足的壓力問題。

如果使用先行編譯標頭`#pragma hdrstop`指示詞時，使用 **/Zm**編譯器旗標，指定較大的值，為先行編譯標頭檔。 否則，請考慮降低平行編譯處理程序，在您的組建數目。 如需詳細資訊，請參閱 < [/Zm （指定先行編譯標頭記憶體配置上限）](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md)。
