---
title: "相容性 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.programs"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "相容性"
  - "相容性, C 執行階段程式庫"
  - "CRT, 相容性"
ms.assetid: 346709cb-edda-4909-9a19-3d253eddb6b7
caps.latest.revision: 18
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 相容性
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

通用 C 執行階段程式庫 \(UCRT\) 支援與 C\+\+ 相容所需的大部分 C 標準程式庫。 除了 \<tgmath.h\> 中所定義的泛型巨集及 \<complex.h\> 中的 Strict 類型相容性之外，其會實作 C99 \(ISO\/IEC 9899:1999\) 程式庫。 UCRT 也會實作 POSIX.1 的大型子集 \(ISO\/IEC 9945\-1:1996，POSIX 系統應用程式開發介面\) C 程式庫，但不全然符合任何特定的 POSIX 標準。  此外，UCRT 會實作數個 Microsoft 特有但不包含在標準之中的函式與巨集。  
  
 Microsoft Visual C\+\+ 實作特有的函式可在 vcruntime 程式庫中找到。  這些函式中有許多僅供內部使用，且無法透過使用者程式碼呼叫。 有一部分會記載在說明中，供偵錯及實作相容性之用。  
  
 C\+\+ 標準在全域命名空間中，會保留以底線開頭的名稱供實作之用。 POSIX 函式雖然位於全域命名空間中，但卻不屬於標準的 C 執行階段程式庫，因此會在 Microsoft 特有函式實作之前加上底線。 為了確保可攜性，UCRT 也能支援預設名稱，但當使用這些名稱的程式碼遭到編譯時，Visual C\+\+ 編譯器仍會發出已被取代的警告。 只有預設 POSIX 名稱已被取代，函式本身仍可繼續使用。 若要停止顯示警告，請先定義 `_CRT_NONSTDC_NO_WARNINGS`，然後再將標頭加入使用原始 POSIX 名稱的程式碼中。  
  
 標準 C 程式庫中有某些函式曾因為誤用參數及未檢查緩衝區而有使用方式不安全的記錄。 這些函式通常是程式碼中安全性問題的來源。 Microsoft 為這些函式建立了一套更安全的版本，可以檢查參數的使用方式，並能在執行階段偵測到問題時，叫用無效參數處理常式。  根據預設，當現行函式有更安全的變體可供使用時，Visual C\+\+ 編譯器便會發出已被取代警告。 當您將程式碼編譯成 C\+\+ 時您可以將 `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` 定義為 1，以排除大部分的警告。 這會使用範本多載來呼叫更安全的變體，同時維護可攜式程式碼。 若要停止顯示警告，請先定義 `_CRT_SECURE_NO_WARNINGS`，然後再將標頭加入使用這些函式的程式碼中。 如需詳細資訊，請參閱[CRT 中的安全性功能](../c-runtime-library/security-features-in-the-crt.md)。  
  
 除了文件中所述有關這些特殊函式的相關資訊之外，UCRT 也相容於 Windows API。  某些函式在 Windows 8 市集應用程式或 Windows 10 上的通用 Windows 應用程式中不受支援。 這些函式列在 [\/ZW 不支援的 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)中，其中將列舉 [Windows 執行階段](http://msdn.microsoft.com/zh-tw/9a1a18b8-9802-4ec5-b9de-0d2dfdf414e9)不支援的函式。  
  
## 相關文章  
  
|標題|描述|  
|--------|--------|  
|[Windows 市集應用程式、Windows 執行階段和 C 執行階段](../c-runtime-library/windows-store-apps-the-windows-runtime-and-the-c-run-time.md)|說明 UCRT 常式與通用 Windows 應用程式或 Windows 市集應用程式不相容的情況。|  
|[符合 ANSI C 標準](../c-runtime-library/ansi-c-compliance.md)|說明 UCRT 中符合標準的命名。|  
|[UNIX](../c-runtime-library/unix.md)|提供移植程式至 UNIX 的指導方針。|  
|[Windows 平台 \(CRT\)](../c-runtime-library/windows-platforms-crt.md)|列出此 CRT 支援的作業系統。|  
|[回溯相容性](../c-runtime-library/backward-compatibility.md)|描述如何將舊的 CRT 名稱對應到新的 CRT 名稱。|  
|[CRT 程式庫功能](../c-runtime-library/crt-library-features.md)|提供 CRT 程式庫 \(.lib\) 檔案和相關聯之編譯器選項的概觀。|