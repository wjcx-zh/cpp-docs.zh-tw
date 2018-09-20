---
title: 1. 簡介 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c42e72bc-0e31-4b1c-b670-cd82673c0c5a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4ce963d312d145e26567a5902f32e45735eb1d89
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46438414"
---
# <a name="1-introduction"></a>1.簡介

這份文件指定編譯器指示詞、 程式庫函式，並可用來指定 C 和 c + + 程式中的共用記憶體平行處理原則的環境變數的集合。 這份文件中所述的功能通稱為*OpenMP C/c + + 應用程式介面 (API)*。 此規格的目標是提供進行平行程式設計的模型可讓程式能夠移植到不同廠商的共用記憶體架構不同。 OpenMP C/c + + API 將會由許多廠商的編譯器支援。 OpenMP 的詳細資訊包括*OpenMP Fortran 應用程式開發介面*，請參閱下列網站：

[http://www.openmp.org](http://www.openmp.org)

指示詞、 程式庫函式和此文件中定義的環境變數可讓使用者建立和管理平行處理程式，同時允許可攜性。 指示詞會擴充 C 和多個資料 (SPMD) 建構、 工作共用建構和同步處理建構，c + + 循序程式設計模型與單一的程式，其提供支援的 「 共用 」 和 「 私有化 」 的資料。 支援 OpenMP C 和 c + + API 的編譯器會包含命令列選項，編譯器就會啟動，並允許所有 OpenMP 編譯器指示詞的解譯。