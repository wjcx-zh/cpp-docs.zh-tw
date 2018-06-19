---
title: 1. 簡介 |Microsoft 文件
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
ms.openlocfilehash: 883af9cb48a0fb13dbb9a758d6f8174096d4c0c3
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33685836"
---
# <a name="1-introduction"></a>1.簡介
這份文件指定編譯器指示詞、 程式庫函式，可用來指定 C 和 c + + 程式中的共用記憶體平行處理原則的環境變數的集合。 這份文件中所述的功能統稱為*OpenMP C/c + + 應用程式介面 (API)*。 此規格的目標是提供進行平行程式設計模型可讓程式能夠移植到不同廠商的共用記憶體架構不同。 OpenMP C/c + + 應用程式開發介面會從許多廠商編譯器支援。 OpenMP 以及詳細的資訊包括*OpenMP Fortran 應用程式開發介面*，可以在下列網站找到：  
  
 [http://www.openmp.org](http://www.openmp.org)  
  
 指示詞，程式庫函式和此文件中定義的環境變數可讓使用者建立及管理平行的程式，同時允許可攜性。 指示詞會擴充 C 和 c + + 循序程式設計模型與單一程式多個資料 (SPMD) 建構、 工作共用建構和同步處理建構，並提供支援的共用和私有化的資料。 支援 OpenMP C 和 c + + 應用程式開發介面的編譯器會包含命令列選項，編譯器就會啟動，並可讓所有 OpenMP 編譯器指示詞的解譯。