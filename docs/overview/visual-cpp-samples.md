---
title: Visual Studio c + + 範例
description: GitHub 上封存的 Visual Studio c + + 範例儲存機制中可用範例的摘要說明。
ms.date: 03/23/2020
ms.technology: cpp-language
ms.assetid: 76798022-5886-48e7-a7f2-f99352b15cbf
ms.openlocfilehash: 56e9cfe72e58a12fb381c88616496820908006c8
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88846364"
---
# <a name="visual-studio-c-samples"></a>Visual Studio c + + 範例

Visual Studio c + + 的範例可在網站上取得。 Microsoft 所產生的多個 c + + 範例會示範多項技術之間的不同功能。 以下是一些尋找其他範例的地方：

- [Microsoft Docs 範例-c + +](/samples/browse/?term=c%2B%2B)

- [GitHub 上的 Windows 範例](https://microsoft.github.io/windows/)

- [Windows 開發人員中心程式碼範例](https://developer.microsoft.com/windows/samples)

- [CodePlex 範例封存](https://archive.codeplex.com/)

- [ADO 程式碼範例](/office/client-developer/access/desktop-database-reference/ado-code-examples-in-microsoft-visual-c)

- [Windows Hardware development samples](/samples/browse/?products=windows-wdk) (Windows 硬體開發範例)

## <a name="archived-c-samples-on-github"></a>GitHub 上封存的 c + + 範例

Visual Studio 在舊版中包含 c + + 範例程式碼。 範例程式碼是隨 Visual Studio 安裝，或以個別下載的形式提供。 檔中的許多文章都參考這些範例。 Visual Studio 不會再安裝。 相反地，您可以在 GitHub 上取得存放庫。 下表包含每個範例的描述，以及存放庫中範例目錄的連結。

[!INCLUDE[note_security_samplecode](includes/note_security_samplecode_md.md)]

## <a name="atl-samples"></a>ATL 範例

### <a name="atl-samples---advanced"></a>ATL 範例-Advanced

| 範例名稱 | 描述 |
|--|--|
| [ActiveDoc](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/Advanced) | 示範如何實作主動式文件伺服程式 (Active Document Server)。 |
| [非同步](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/Advanced) | 從 URL 非同步載入資料。 |
| [ATLButton](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/Advanced) | 建立會根據本身狀態可顯示三種不同點陣圖的按鈕。 |
| [ATLDuck](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/Advanced) | 示範以 ATL 控制項使用連接點。 |
| [ATLSecurity](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/Advanced) | 顯示如何使用 ATL 安全類別來檢查安全設定。 |
| [ATLTraceTool](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/Advanced) | 顯示宏所產生的輸出 `ATLTRACE2` 。 |
| [[連接]](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/Advanced) | 說明在多執行緒環境中連接點 (IConnectionPointContainer 和 IConnectionPoint 介面) 的實作與使用。 |
| [CThreadPool](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/Advanced) | 顯示如何在應用程式裡使用執行緒集區和實作執行緒集區如何改善應用程式的效能。 |
| [DCOM](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/Advanced) | 示範如何從在不同電腦上執行的多個用戶端，呼叫在 Windows 服務) 中執行的 COM 物件 (。 |
| [MFCATL](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/Advanced) | 說明 ATL COM 物件如何用於 MFC 伺服器 EXE。 |

### <a name="atl-samples---controls"></a>ATL 範例-控制項

| 範例名稱 | 描述 |
|--|--|
| [ATLFire](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/Controls) | 示範使用 ATL 建置視窗化控制項的方法。 |
| [CDInfo](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/Controls) | 播放 CD 音訊播放軌，並顯示工具提示和圓形圖顯示中的曲目相關資訊。 |
| [Circ](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/Controls) | 建立示範屬性頁和畫圓的控制項。 |
| [Polygon](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/Controls) | 建置實作自訂屬性 (Property)、事件、屬性頁和物件安全的控制項。 |
| [SubEdit](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/Controls) | 建立 Superclass 的 Windows 控制項。 |

### <a name="atl-samples---general"></a>ATL 範例-一般

| 範例名稱 | 描述 |
|--|--|
| [ATLCollections](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/General) | 示範如何使用 `ICollectionOnSTLImpl` 和和 `CComEnumOnSTL` 自訂複寫原則類別的執行。 |
| [ATLCon](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/General) | 示範一個簡易控制項容器。 |
| [ATLSafeArray](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/General) | 示範如何使用建立和維護，以及 `SAFEARRAY` `CComSafeArray` 如何 `SAFEARRAY` 從元件傳遞至腳本。 |
| [AutoThread](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/General) | 示範如何使用 `CComAutoThreadModule` 類別。 |
| [Beeper](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/General) | 針對的集合/列舉，執行卸載的介面 `BSTR` 。 |
| [CircColl](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/General) | 實作使用 ATL 和 Standard C++ 程式庫之物件的集合/列舉型別 (Enumeration)。 |
| [COMMap](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/General) | 示範具有編譯器 COM 支援的 COM 介面對應項巨集。 |
| [CustomString](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/General) | 示範如何使用自訂記憶體配置器， `CStringT` 以改善多執行緒應用程式中的效能。 |
| [DispSink](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/General) | 示範在分派介面使用連接點。 |

### <a name="atl-samples---oledb---consumer"></a>ATL 範例-OLEDB-取用者

| 範例名稱 | 描述 |
|--|--|
| [CatDB](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer) | 顯示 OLE DB 提供者的結構描述資訊，例如表格和欄位。 |
| [DBViewer](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer) | 示範一個中介層應用程式，該應用程式依賴 `CManualAccessor` 類別來完全掌控應用程式的資料系結。 |
| [DynamicConsumer](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer) | 示範使用動態存取子和結構描述資料列集類別來讀取來自資料庫的中繼資料。 |
| [MultiRead](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer) | 使用多個執行緒讀取資料庫中的資料表。 |

### <a name="atl-samples---oledb---provider"></a>ATL 範例-OLEDB-提供者

| 範例名稱 | 描述 |
|--|--|
| [AdvancedPV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider) | 實行可更新的 OLE DB 提供者。 示範一些進階的技巧。 |
| [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider) | 執行可更新的 (讀取/寫入) OLE DB 提供者。 |

## <a name="clr-and-language-samples---windows-forms"></a>CLR 和語言範例-Windows Forms

| 範例名稱 | 描述 |
|--|--|
| [BirthdayPicker](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/Language/Windows%20Forms) | 示範 .NET Framework 資源機制在 C++ 應用程式中的使用方式， 此外，本範例還會示範某些 Window Form 通用元件。 |
| [計算機](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/Language/Windows%20Forms) | 使用 C++ 和 .NET Framework Windows Form 類別來實作簡單的袖珍計算機。 |
| 使用 MFC 的自由曲線 ()  | 實作 MFC 的 Scribble 範例，已經過更新和擴充以包含新的 .NET 功能。 |
| [Scribble (Windows Forms)](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/Language/General) | Scribble 範例的 Windows Form 實作，已更新並擴充成包含新的 .NET 功能。 |
| [STLCLR](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/CLR/stlclr/StlClr%20Sample) | 示範當使用 STL/CLR 程式庫時可用的某些功能。 |

## <a name="com-events-samples"></a>COM 事件範例

| 範例名稱 | 描述 |
|--|--|
| [COMEvents](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples) | 示範使用 COM 的事件處理。 |

## <a name="comtypelibfor7-samples"></a>ComTypeLibfor7 範例

| 範例名稱 | 描述 |
|--|--|
| [ACDual](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ComTypeLibfor7) | 將雙重介面 (Dual Interface) 加入至 Automation 應用程式。 |
| [ADOSamp](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ComTypeLibfor7) | 實作三層 (Three-Tier) 的主從架構應用程式。 |
| [AllInOne](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ComTypeLibfor7) | 在一個 MFC 應用程式中實作一個使用 ATL、公開 STL 集合物件並由編譯器 COM 支援控制的伺服程式。 |
| [COMMap](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ComTypeLibfor7) | 示範具有編譯器 COM 支援的 COM 介面對應項巨集。 |
| [[連接]](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ComTypeLibfor7) | 說明在 `IConnectionPointContainer` `IConnectionPoint` 多執行緒環境中)  (和介面的連接點使用和執行。 |
| [DCOM](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ComTypeLibfor7) | 示範如何從在不同電腦上執行的多個用戶端，呼叫在 Windows 服務) 中執行的 COM 物件 (。 |
| [FreeThrd](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ComTypeLibfor7) | 示範一個多重執行緒用戶端和具有編譯器 COM 支援的無限制執行緒伺服程式。 |
| [InProc](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ComTypeLibfor7) | 示範具有編譯器 COM 支援的同處理序 (In-Process) Automation 伺服器應用程式。 |
| [Labrador](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ComTypeLibfor7) | 執行沒有任何使用者介面的 EXE 伺服器。 |
| [MFCCalc](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ComTypeLibfor7) | 示範一個具有編譯器 COM 支援的 Automation 伺服器應用程式。 |

## <a name="compiler-samples"></a>編譯器範例

### <a name="compiler-samples---general"></a>編譯器範例-一般

| 範例名稱 | 描述 |
|--|--|
| [ccWrapper](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/Compiler) | 示範如何將其他編譯器的 C/C++ 編譯器旗標對應到 Visual C++ 編譯器 (cl.exe)。 |

### <a name="compiler-samples---masm"></a>編譯器範例-MASM

| 範例名稱 | 描述 |
|--|--|
| [EuclidStep1](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/Compiler/MASM) | 這是一個純 C 專案，示範使用 Euclid 的演算法來找出最大公因數。 |
| [EuclidStep2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/Compiler/MASM) | EuclidStep1 的延伸模組，其為混合的 C 和 MASM 專案。 Euclid 演算法的核心會從檔案移至檔案 *`.c`* *`.asm`* ，並將檔案呼叫至檔案中 *`.c`* *`.asm`* 。 |
| [PrimesStep1](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/Compiler/MASM) | 單純的 C 專案，示範用來尋找質數的 Eratosthenes Sieve。 |
| [PrimesStep2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/Compiler/MASM) | PrimesStep1 的延伸模組，其為將核心演算法移至檔案的混合 C 和 MASM 專案 *`.asm`* 。 |
| [PrimesStep3](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/Compiler/MASM) | PrimesStep2 的延伸模組，它會加入個別的 C 標頭檔和包含檔案， *`.asm`* 以宣告 extern 函數和全域資料結構。 |

## <a name="crt-samples"></a>CRT 範例

| 範例名稱 | 描述 |
|--|--|
| [CPUID](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt) | 判斷正在執行之 CPU 的效能。 |
| [CRT_Dbg1](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt) | 說明 C 執行階段程式庫的基本偵錯功能。 |
| [CRT_Dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt) | 示範 C Run-Time 偵錯攔截函式。 |
| [DFACObjs](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt) | 顯示如何使用 _CrtDoForAllClientObjects C 執行階段函式來重複執行用戶端物件的連結串列。 |
| [Report](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt) | 說明 C Run-Time 偵錯回報函式。 |
| [RTC](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt) | 示範執行階段錯誤檢查功能。 |
| [SecureCRT](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt) | 這個範例示範如何將使用已取代的 CRT 功能的程式碼升級，增加程式碼安全性。 |

## <a name="debugging-samples"></a>調試範例

| 範例名稱 | 描述 |
|--|--|
| [EEAddIn](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples) | 這個函式會使用運算式評估工具增益集 (Expression Evaluator Add-In) API 來擴充原生 (Native) 偵錯工具的運算式評估工具。 |

## <a name="fusion-samples"></a>融合範例

| 範例名稱 | 描述 |
|--|--|
| [TraceMan](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples) | 提供有關應用程式相依元件的資訊，以及原生融合快取中元件的狀態，以人類看得懂的形式。 |

## <a name="hilo-sample"></a>Hilo 範例

| 範例名稱 | 描述 |
|--|--|
| [希洛](https://github.com/Microsoft/VCSamples/tree/master/VC2013Samples/Hilo) | Hilo 是一系列的文章和範例應用程式。 它們示範 Windows 7、Visual Studio 和 c + + 的強大功能，以建立高效能、回應迅速的用戶端應用程式。 Hilo 提供原始程式碼和指引，可協助您設計和開發您自己的引人注目、觸控式 Windows 應用程式。<br/><br/>此範例已針對 Visual Studio 2013 更新。 它包含 *AsyncLoaderMemoryManager .cpp* 檔案的熱修正 (行36和 37) ，可解決常見的損毀問題。 |

## <a name="international-samples"></a>國際範例

| 範例名稱 | 描述 |
|--|--|
| [IME](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/International) | 示範如何控制輸入法 (IME) 模式，以及如何實作 IME 層級 3。 |
| [SatDLL](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/International) | 示範在 Win32 應用程式中實作多語系資源的建議方式。 |
| [UniRes](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/International) | 示範 Unicode 資源檔的用法。 |

## <a name="language-samples---general"></a>語言範例-一般

| 範例名稱 | 描述 |
|--|--|
| [資料](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/Language) | 示範 SQL 資料庫的簡單存取。 |
| [MEDriver](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/Language) | 其中將說明如何透過由 COM 伺服器型別程式庫自動產生的 .NET Framework 包裝函式來使用 COM 事件 (從 Unmanaged COM 伺服器引發)。 |
| [Nile](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/Language) | 示範 ASP.NET Web Forms 和 ASP.NET Web 服務。 |
| [QStat](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/Language/General) | 示範如何建立一個可包裝 COM 物件存取權限、並向 .NET Framework 用戶端公開其功能的 DLL。 |
| [Scribble](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/Language/General) | 示範如何使用 C++/CLI 和 .NET Framework 類別來開發 Windows Form MDI 應用程式。 |
| [TilePuzzle](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/Language/General) | 示範 Managed 元件 (以 C++ 和 C# 撰寫) 和原生元件 (以採用 COM 屬性的 C++ 所撰寫) 之間的互通性。 |

## <a name="mfc-samples"></a>MFC 範例

### <a name="mfc-samples---advanced"></a>MFC 範例-Advanced

| 範例名稱 | 描述 |
|--|--|
| [收集](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced) | 示範 MFC C++ 範本架構的集合類別以及標準的預先建置集合類別。 |
| [立方體](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced) | 使用 MFC 裝置內容和 OpenGL 資源內容的 OpenGL 應用程式。 |
| [DLLHusk](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced) | 提供 MFC 程式庫的 DLL 版本給應用程式和自訂的 DLL 共用。 |
| [DLLScreenCap](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced) | 一個可以靜態或動態連結到 MFC 程式庫之規則 DLL。 |
| [MTGDI](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced) | 示範使用架構對文件與檢視的單一文件介面 (SDI) 支援，在多個執行緒間共用 GDI 資源。 |
| [MTMDI](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced) | 說明多執行緒，其中使用介面事件可以在不同的使用介面執行緒中處理。 |
| [MTRecalc](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced) | 多執行緒圖解，其中會在背景工作執行緒中完成重新計算。 |
| [Mutex](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced) | 以對話方塊為基礎的應用程式會建立兩個 `CWinThread` 物件，並使用它們來在使用者的控制項下進行工作。 |
| [Speakn](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced) | 使用使用者定義的資源展示多媒體音效。 |

### <a name="mfc-samples---controls"></a>MFC 範例-控制項

| 範例名稱 | 說明 |
|--|--|
| [Button](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/controls) | 示範如何使用就地活動功能表、內建屬性頁，以及 About box 控制項選項。 |
| [Circ](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/controls) | 示範 ActiveX 控制項基本概念。 這些包括控制項繪製、內建和自訂屬性、股票和自訂事件、色彩和字型的使用、股票字型屬性頁、預設屬性頁，以及版本控制。 |
| [CmnCtrl](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/controls) | 示範 w x 上 MFC 可用的一些新控制項：命令連結按鈕 (`CButton`) 、呼機控制項 (`CPagerCtrl`) 、分割按鈕 (`CSplitButton`) ，以及網路位址控制項 (`CNetAddressCtrl`) 。 |
| [Contain](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/controls) | 示範視覺化編輯容器應用程式。 |
| [映像](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/controls) | 示範如何使用 MFC 來建立 ActiveX 控制項，以非同步方式下載資料。 |
| [許可](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/controls) | 一個強制設計階段和執行階段授權使用的控制項。 |
| [當地語系化](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/controls) | 一個當地語系化使用者介面的控制項，它將展示用於當地語系化之個別型別程式庫和資源動態聯結程式庫 (DLL) 的使用方式。 |
| [NetAddr](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/controls) | 示範 Windows Vista「網路位址驗證器」控制項的用法。 |
| [朋友](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/controls) | 會顯示調色盤色彩的控制項。 它會示範唯讀屬性、永續性 Get/Set 屬性、永續性參數化屬性以及圖片屬性。 |
| [推送](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/controls) | 從 Windows 主控描繪按鈕控制項子類別化的控制項。 它會示範內建屬性、自訂事件和圖片位置。 |
| [RegSvr](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/controls) | 示範自我登錄程式碼的引動過程。 |
| [SpinDial](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/controls) | 一個擁有微調撥號視覺外觀的控制項，可展示屬性頁資料驗證。 |
| [TestHelp](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/controls) | 一個擁有自己的說明檔案和工具提示的 ActiveX 控制項。 |
| [Time](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/controls) | 一個在執行階段不可見，且會在設定的時間間隔引發計時器事件的控制項。 示範告知功能和環境屬性 (Ambient Property)。 |
| [.Xlist](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/controls) | 一個從 Windows 清單方塊子類別化、可顯示文字或點陣圖項目的控制項。 |

### <a name="mfc-samples---general"></a>MFC 範例-一般

| 範例名稱 | 描述 |
|--|--|
| [ClipArt](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 美工圖案目錄包含可用來自訂應用程式外觀的範例資源。 |
| [CmnCtrl1](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 示範如何使用 MFC 類別來建立和變更 Windows 通用控制項的樣式 (第一部分)。 |
| [CmnCtrl2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 示範如何使用 MFC 類別來建立和變更 Windows 通用控制項的樣式 (第二部分)。 |
| [CTaskDialog](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 示範類別的各種功能 `CTaskDialog` 。 |
| [CtrlBars](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 自訂工具列、狀態列、對話方塊列和浮動工具板。 |
| [CtrlTest](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 主控描繪的清單方塊、功能表、自訂控制項、點陣圖按鈕和微調控制項。 |
| [DBVList](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 使用 `CListView` 和 `CDaoRecordset` 類別來執行清單視圖通用控制項可用的虛擬清單視圖功能。 |
| [DIBLook](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 示範 DIB 和色板的用法。 |
| [DlgCbr32](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 將工具列和狀態列加入至對話方塊架構應用程式。 |
| [DlgTempl](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 示範動態建立對話方塊範本。 |
| [DockTool](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 可停駐的拖曳和浮動工具列。 |
| [Dynamenu](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 動態修改功能表的項目清單；處理編譯時間未知的命令；並且更新這類命令的狀態列命令提示字元。 |
| [FileDlgWatcher](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 建立自訂對話方塊，以說明當您建立時所產生的事件 `CFileDialog` 。 |
| [您好](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 示範具有功能表和 [關於] 對話方塊的單一應用程式視窗。 |
| [HelloApp](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 最小的 MFC 範例，示範讓視窗顯示於畫面上所需的數行程式碼。 |
| [ListHdr](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 示範如何使用通用控制項 MFC 類別 `CListCtrl` 和 `CHeaderCtrl` 。 |
| [MDI](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 不使用檔和視圖的 MDI 應用程式。 |
| [MDIDocVw](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 使用文件/檢視架構的更新版 MDI 範例。 |
| [MMXSwarm](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 示範如何使用 `CImage` 、 **`__m64`** 資料類型，以及與裝置無關的點陣圖 (dib) 。 |
| [模 態](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 示範如何使用 MFC `CDialog` 物件做為非強制回應對話方塊。 |
| [Multipad](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 簡單的文字編輯器，可讓使用者同時開啟及編輯多個文字檔。 |
| [Npp](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 示範如何使用類似記事本的 (SDI) 應用程式來執行介面。 它可讓您編輯文字訊息，並透過 Windows 訊息 API 或 MAPI 將訊息傳送給其他使用者或其他系統。 |
| [PropDlg](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 屬性工作表 (對話方塊)。 |
| [RowList](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 說明清單檢視通用控制項中的整列選取。 |
| [Scribble](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 簡單示範 MFC 強大的功能。 |
| [SimpleImage](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 示範載入、調整大小、轉換和儲存影像。 |
| [SnapVw](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 顯示如何使用 MDI 子框架視窗中的屬性頁。 |
| [Spiro](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 示範如何 `CImageList` 在需要動畫效果的應用程式中使用記憶體顯示內容的遊戲。 |
| [Tracker](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 示範各種 `CRectTracker` 樣式和選項。 |
| [VariantUse](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 示範 Variant 資料型別的用法。 |
| [ViewEx](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 多個檢視、捲動檢視、分隔視窗。 |

### <a name="mfc-samples---internet"></a>MFC 範例-網際網路

| 範例名稱 | 描述 |
|--|--|
| [DHTMLExplore](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/internet) | 展示處理 DHTML 事件和使用 DHTML DDX。 |
| [HTMLEdit](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/internet) | 包裝 Internet Explorer MSHTML 編輯器控制項。 |
| [MFCIE](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/internet) | 示範 MFC `CHtmlView` 和 `CReBar` 類別。 |
| [排程器](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/internet) | 示範如何使用 Visual C++ 程式庫類別建立 HTML 架構對話方塊。 |

### <a name="mfc-samples---ole"></a>MFC 範例-OLE

| 範例名稱 | 描述 |
|--|--|
| [ACDual](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/ole) | 示範如何將雙重介面支援加入至一個 MFC 架構的 Automation 伺服應用程式。 |
| [AutoClik](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/ole) | 說明 Automation 功能。 包含 AUTODRIV 這個可以驅動 AUTOCLIK 範例應用程式的簡單用戶端應用程式。 |
| [CalcDriv](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/ole) | Automation 用戶端。 |
| [DrawCli](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/ole) | 全功能的物件導向繪圖應用程式，同時也是一個 ActiveX 視覺化編輯容器。 |
| [HierSvr](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/ole) | 示範伺服器應用程式與 OLE 拖放。 |
| [InProc](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/ole) | 一個可當成 DLL 載入於用戶端位址空間的同處理序 Automation 伺服程式。 |
| [IPDrive](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/ole) | 一個驅動 INPROC 範例應用程式的簡單 Automation 用戶端應用程式。 |
| [MFCBind](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/ole) | 示範如何建立主動式文件 (即是先前的 DocObject) 容器。 |
| [MFCCalc](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/ole) | 一個實作簡易的計算機的 Automation 伺服程式。 |
| [OClient](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/ole) | 可以執行拖放的 ActiveX 視覺化編輯容器應用程式。 |
| [OLEView](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/ole) | 透過自訂的 OLE 介面來實作一個 OLE 物件瀏覽器。 |
| [SuperPad](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/ole) | 示範使用 CEditView 編輯文字的視覺化編輯服務器。 |
| [TstCon](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/ole) | 使用 OLE 內嵌的 MFC 支援來實作一個 ActiveX 控制項容器。 您可以使用 TSTCON 來測試 ActiveX 控制項、變更其屬性和叫用其方法。 |
| [寫字 板](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/ole) | 使用 Rich Edit 控制項的 MFC 支援來建立一個基本的文字處理器。 |

### <a name="mfc-samples---utility"></a>MFC 範例-公用程式

| 範例名稱 | 描述 |
|--|--|
| [GUIDGen](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/utility) | 產生全域唯一識別碼的簡單對話型 MFC 應用程式。 |
| [Makehm](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/utility) | 產生資源識別與說明主題代碼 (Help Context) 之間對應的主控台應用程式 (Console Application)。 |

### <a name="mfc-samples---visual-c-2008-feature-pack"></a>MFC 範例-Visual C++ 2008 Feature Pack

| 範例名稱 | 描述 |
|--|--|
| [CustomPages](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 示範如何將自訂頁面加入至工具列自訂對話方塊。 |
| [DesktopAlertDemo](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 示範如何執行桌面警示對話方塊， (類似于立即訊息應用程式) 的對話方塊。 |
| [DlgToolTips](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 示範如何為對話方塊上的控制項實作進階工具提示。 |
| [DrawClient](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 示範如何將功能區的支援整合至具有編輯容器支援的繪圖應用程式。 |
| [DynamicMenu](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 示範如何在執行階段動態更新功能表列上的功能表和快顯功能表。 |
| [總管](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 示範如何執行類似檔案總管的檔案系統 explorer。 它具有類似的使用者介面元素和功能。 |
| [IEDemo](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 示範如何實作與 Internet Explorer 類似、具有類似使用者介面項目和功能的應用程式。 |
| [MDITabsDemo](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 示範如何建立使用新索引標籤式 MDI 文件介面 (而非傳統 MDI 子視窗) 的應用程式。 |
| [MenuSubSet](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 示範如何在應用程式啟動時動態移除特定功能表項目和子功能表。 |
| [MSMoneyDemo](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 示範如何使用 MFC 建立與 Microsoft Money 類似的使用者介面。 |
| [MSOffice2007Demo](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 示範如何實作與 Office 2007 應用程式類似、具有類似使用者介面項目和類似有限功能的編輯器應用程式。 MSOffice2007Demo 範例會執行完整的功能區使用者介面，與 Office 2007 應用程式非常類似。 某些功能區元素會連接到應用程式中的功能。 |
| [NewControls](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 示範 MFC 中所執行之許多控制項的功能。 這些控制項包括可自訂的按鈕、色彩選擇器控制項和調色板、字型選擇器、影像編輯器、屬性方格、遮罩的編輯控制項，以及 shell 清單和樹狀目錄控制項。 |
| [OutlookDemo](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 示範如何建立與 Outlook 2003/2007 類似的應用程式。 |
| [OutlookMultiViews](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 示範如何在 SDI 應用程式中對單一文件切換多個檢視。 本範例使用 Outlook 功能區控制項列出可用的檢視，以及在這些檢視之間進行切換。 |
| [OwnerDrawMenu](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 說明如何動態描繪快顯功能表項目。 |
| [PaletteDemo](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 示範如何建立具有主控描繪資訊區域的多欄工具列。 按一下 [標準] 工具列上的 [2]、[3] 或 [4] 按鈕，在執行時間變更自訂工具列的欄數。 |
| [PropSheetDemo](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 示範下列類型的屬性工作表控制項：簡單、索引標籤於左側、樹狀目錄控制項於左側、OneNote 樣式索引標籤、項目清單於左側。 |
| [RebarTest](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 示範裝載工具列的可自訂 Rebar 控制項。 |
| [RibbonGadgets](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 示範可裝載於功能區控制項的各種控制項。 在主框架底部，您可以找到原始程式碼視窗和原始程式碼文字，其中概述如何建立特定的小工具。 |
| [RibbonMDI](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 示範功能區控制項搭配多重文件介面的用法。 |
| [RollupPane](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 示範會自動向上捲動的浮動「資訊」窗格。 您可以按下浮動窗格標題的固定按鈕，開啟和關閉捲動功能。 |
| [SetPaneSize](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 示範如何以程式設計方式設定停駐窗格大小。 |
| [滑桿](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 示範如何實作裝載外部控制項的工具列按鈕。 |
| [StateCollection](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 示範如何實作一個會儲存及載入功能表列、工具列和停駐視窗不同狀態的應用程式。 |
| [StatusBarDemo](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 示範如何將各種進階控制項加入至狀態列。 |
| [TabbedView](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 示範如何建立包含多個索引標籤式檢視的檢視，例如 Excel 活頁簿中的索引標籤。 |
| [TabControl](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 示範 MFC 索引標籤控制項，以及使用不同屬性和視覺管理員時其不同的外觀。 |
| [TasksPane](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 示範 MFC 工作窗格類別，以及使用各種屬性和視覺管理員時其不同的外觀。 |
| [ToolbarDateTimePicker](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 示範如何將日期/時間選擇器控制項與工具列整合。 |
| [ToolTipDemo](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 示範如何使用進階 MFC 工具提示功能。 |
| [TrayMenu](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 說明使用 MFC 控制列功能表搭配系統匣圖示的功能。 它類似于顯示器右下角的通知圖示。 |
| [VisualStudioDemo](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 示範如何使用 Visual Studio 的許多相同使用者介面特性和功能來執行應用程式。 其中會示範許多 Visual Studio 的使用者介面元素，包括可自訂的銜接功能表列、工具列和視窗。 |
| [寫字 板](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 示範如何實作模仿 WordPad 功能 (包括使用者介面項目及部分功能) 的應用程式。 |
| [WorkSpaceToolBar](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 示範如何將工具列加入至停駐窗格。 它類似于 Visual Studio 方案總管中的工具列。 |

### <a name="mfc-samples---windows-touch"></a>MFC 範例-Windows Touch

| 範例名稱 | 描述 |
|--|--|
| [GestureDemo](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/WindowsTouch) | 示範 MFC 中的 Windows Touch 支援 (需要觸控硬體)。 |
| [TouchDemo](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/WindowsTouch) | 示範 MFC 中的 Windows Touch 支援 (需要觸控硬體)。 |

## <a name="odbc-samples"></a>ODBC 範例

| 範例名稱 | 描述 |
|--|--|
| [odbcsql](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/ODBC%20Database%20sample) | 這個範例會示範如何使用 ODBC Api 來連接及存取資料庫。 |

## <a name="os-samples"></a>OS 範例

| 範例名稱 | 描述 |
|--|--|
| [GetImage](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples) | 示範 Windows 影像擷取 (WIA) 應用程式開發介面 (Application Programming Interface，API)。 |

## <a name="unix-samples"></a>Unix 範例

| 範例名稱 | 描述 |
|--|--|
| [Unix - ccWrapper](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples) | 示範會將 Sun Forte 和 gcc 編譯器的旗標對應到 Microsoft Visual C++ 編譯器 (cl.exe) 的包裝函式。 |

## <a name="windows-8-samples"></a>Windows 8 範例

Windows 8 範例套件包含針對 Windows 8 開發和更新的所有應用程式程式碼範例。 範例套件提供便利的方法，讓您一次下載所有範例。 此範例套件中的範例可在 c #、c + +、VB.NET 和 JavaScript 中使用。 Windows 範例庫包含的程式碼範例，可執行 Windows 8 和 Windows Server 2012 中提供的各種新程式設計模型、平臺、功能和元件。 這些可下載的範例包含 Visual Studio 的解決方案 (*.sln*) 檔、來源檔案、資產、資源，以及編譯和成功執行所需的中繼資料。

如需詳細資訊，請閱讀每個範例中所示範的程式設計模型、平臺、語言和 Api。 請參閱 Windows 開發人員中心提供的 Windows 8 檔中所提供的指引、教學課程和參考文章。 這些範例會依原樣提供，以示範 Windows 8 和 Windows Server 2012 的程式設計模型和功能 Api 的功能。

| 範例名稱 | 描述 |
|--|--|
| [背景傳輸範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範 Windows 執行階段應用程式之背景傳輸 API 的易用、成本感知和彈性的行為。 提供的範例案例涵蓋檔案下載和上傳。 |
| [CryptoWinRT 範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例說明如何使用新的密碼編譯 Api。 |
| [列印範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 這個範例會示範應用程式如何整合 Windows 列印體驗。 此範例中示範的案例包括：使用常用鍵列和列印合約從應用程式列印、從應用程式體驗中進行列印等等。 |
| [HttpClient 範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何使用 HttpClient 類別和 IXMLHTTPRequest2 介面，從 HTTP 伺服器使用 Windows 執行階段所提供的網路功能，來上傳和下載各種類型的內容。 |
| [加速計感應器範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例說明如何使用 `Windows.Devices.Sensors.Accelerometer` API。 這個範例可讓使用者依據 X 軸、Y 軸和 Z 軸，同時針對3軸加速計來查看加速的強制。 您可以選擇三種案例的其中一種。 |
| [帳戶圖片名稱範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 這個範例示範取得目前登入之使用者名稱的不同方式。 它也會示範如何取得及設定用於使用者磚的影像。 |
| [應用程式設定範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何使用 ApplicationSettings API 和設定 flyouts，將應用程式的設定 UI 與設定快速鍵整合。 此範例會使用 `Windows.UI.ApplicationSettings` 命名空間和 `WinJS.UI.SettingsFlyout` 。 |
| [適用于相機的 Windows Store 裝置應用程式範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 這個範例示範如何建立攝影機的 Windows Store 裝置應用程式。 Windows Store 裝置應用程式是由 IHV 或 OEM 提供，以區分特定相機的捕獲體驗。 |
| [開始使用 c + + 簡單的 blog reader 範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何使用 XAML 來定義使用者介面，以原生 c + + 開發 Windows Store 應用程式的一些基本原則。 它是 Windows 開發人員中心所討論之應用程式的完整運作版本。 |
| [讀取和寫入資料範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例說明如何使用 DataReader 和 >datawriter 類別來儲存和取出資料。 |
| [應用程式資料範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例說明如何使用 Windows 執行階段的應用程式資料 Api，來儲存和取出每個使用者和 Windows Store 應用程式專屬的資料。 應用程式資料包含會話狀態、使用者喜好設定和其他設定。 |
| [自訂驅動程式存取範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例說明如何使用 CreateDeviceAccessInstance 和 IDeviceIoControl 來存取特製化裝置。 |
| [XAML ListView 和 GridView essentials 範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 這個範例示範如何使用 GridView 和 ListView 控制項。 |
| [動畫計量範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 這個範例示範如何在中使用動畫計量 Api `Windows.UI.Core` 。AnimationMetrics，以存取在 Windows 動畫庫中定義動畫的原始參數。 |
| [播放管理員 msAudioCategory 範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何為音訊影片 (AV) 串流中選取正確的 msAudioCategory 類別，以將其設定為音訊播放串流。 |
| [XAML DirectX 3D 診斷遊戲範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何在 c + + 應用程式中使用 DirectX (Direct3D 11.1、Direct2D、XInput 和 XAudio2) 和 XAML，來執行簡單的第一員3-d 遊戲。 XAML 適用于列印頭顯示和遊戲狀態訊息。 |
| [XAML 滾動、移動和縮放範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 這個範例示範如何使用 ScrollViewer 控制項來平移和縮放。 |
| [XAML FlipView 控制項範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 這個範例會示範如何使用 FlipView 控制項，讓使用者可以透過集合來切換。 |
| [陀螺儀感應器範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例說明如何使用 `Windows.Devices.Sensors.Gyrometer` API。 這個範例可讓使用者沿著 X 軸、Y 軸和 Z 軸，同時針對3軸陀螺儀來查看角度的速度。 |
| [適用于印表機的裝置應用程式 SDK 範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 這個範例示範如何建立印表機的裝置應用程式，此應用程式可從磚合約、Windows.search 合約，以及 backgroundTask 所顯示的快顯通知，以回應列印驅動程式事件。 |
| [背景工作範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例說明如何使用 Windows 執行階段背景工作 API 來建立和註冊背景工作。 系統或時間事件會觸發背景工作，且可以受限於一或多個條件。 |
| [StreamSocket 範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 這個範例會使用 Windows 執行階段所提供的網路功能，來示範 StreamSocket 類別的基本概念。 此範例的用戶端元件會建立 TCP 通訊端來建立網路連線、使用通訊端來傳送資料，以及執行其他工作。 |
| [排程的通知範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何針對應用程式使用排程和週期性的磚更新和快顯通知。 此功能可讓您指定傳遞通知的精確時間，即使應用程式未執行也是如此。 |
| [播放管理員附屬範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何為音訊影片串流選取正確的 msAudioCategory 類別，以將其設定為音訊播放串流。 |
| [OrientationSensor 範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例說明如何使用 `Windows.Devices.Sensors.OrientationSensor` API。 它可讓使用者查看反映目前裝置方向的旋轉矩陣和四元數值。 |
| [檔案存取範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 這個範例會示範如何建立、讀取、寫入、複製和刪除檔案、如何取出檔案屬性，以及如何追蹤檔案或資料夾，讓您的應用程式可以再次存取它。 此範例會使用 `Windows.Storage` 和 `Windows.Storage.AccessCache` API。 |
| [卸除式存放裝置範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 卸除式存放裝置範例示範如何在卸除式存放裝置裝置之間傳輸檔案。 此範例需要有連接到系統的卸除式存放裝置裝置，例如相機、媒體播放機、行動電話或 USB 拇指磁片磁碟機。 |
| [XAML SurfaceImageSource DirectX interop 範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何使用，將 `SurfaceImageSource` DirectX 內容包含在您的 XAML 應用程式中。 這個範例會使用 c + + 和 c #。 |
| [ (Windows 8) 連接至 Websocket 範例 ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何在已連線的 Windows Store 應用程式中使用 Websocket。 此範例涵蓋基本功能，例如如何建立連接、傳送和接收資料，以及關閉連接。 |
| [設定媒體範例 (Windows 8) 的金鑰 ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 這個範例示範如何設定鍵盤上的硬體媒體按鍵。 然後，如何使用設定的按鍵來控制音訊視頻串流，方法是按或按一下 [播放]、[暫停]、[停止] 等等。 |
| [XAML 特性動畫範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何在您的應用程式中使用內建的特質動畫。 |
| [快顯通知範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何使用快顯通知：在螢幕右上角顯示為快顯通知的通知。 使用者可以選取快顯 (觸控，或按一下 [) ] 來啟動相關聯的應用程式。 |
| [連絡人選擇器應用程式範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何使用連絡人選擇器來選取一或多個連絡人。 它也包含連絡人選擇器 Api 的基本執行，以示範如何顯示使用者的連絡人清單。 |
| [DirectX 大理石迷宮遊戲範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 這個範例示範如何使用 DirectX 建立基本的3D 遊戲。 這項遊戲是一個簡單的 labyrinth 遊戲，其中玩家面臨著使用傾斜控制項來透過迷宮的迷宮來變換大理石。 |
| [DirectX 明信片應用程式範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何使用 DirectX 搭配 c + + 來執行簡單的 Windows Store 應用程式，以使用 DirectX 和 XAML interop 來建立明信片。 |
| [DirectX 3D 診斷遊戲範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何在 c + + 應用程式中使用 DirectX (Direct3D 11.1、Direct2D、XInput 和 XAudio2) ，來執行簡單的第一員3-d 遊戲。 |
| [XAML AppBar 控制項範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 這個範例示範如何使用 AppBar 控制項，向使用者呈現導覽、命令和工具。 依預設會隱藏應用程式行，並且會在使用者從畫面的頂端或下邊緣滑動手指時出現。 |
| [日期和時間格式範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 這個範例會示範如何使用命名空間中的 DateTimeFormatter 類別 `Windows.Globalization.DateTimeFormatting` ，根據使用者的喜好設定來顯示日期和時間。 |
| [次要磚範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何釘選和使用次要磚。 這是在應用程式中直接存取特定、非預設區段或體驗的磚，例如儲存的遊戲，或社交網路應用程式中的特定朋友。 |
| [輸入觸控點擊測試範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例使用多邊形圖案謎題來示範如何處理指標輸入、執行觸控輸入的自訂點擊測試，以及使用 c + + 和 DirectX 在 Windows Store 應用程式中處理操作。 |
| [網路資訊範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何使用 Windows 執行階段的網路資訊 Api。 |
| [輸入簡化的筆墨範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何在 Windows Store 應用程式中使用筆墨功能。 |
| [StorageDataSource 和 GetVirtualizedFilesVector 範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何在使用者的圖片庫中取出並顯示影像。 |
| [以邊緣為基礎的手勢調用範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何使用類別來接聽以 edge 為基礎之 UI 中發生的事件 `EdgeGesture` 。 |
| [檢查目前的會話是否為遠端範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何使用 `Windows.System.RemoteDesktop` API。 |
| [應用程式資源和當地語系化範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何使用應用程式資源，將可當地語系化的內容與應用程式程式碼分開。 此範例會使用 `Windows.ApplicationModel.Resources.Core` 和 `Windows.Globalization` 命名空間，以及 `WinJS.Resources` 。 |
| [內容功能表範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 這個範例會示範如何建立內容功能表，以及如何取代文字的預設內容功能表。 此範例會使用 `Windows.UI.Popups` API，包括 PopupMenu 和 oncoNtextmenu 事件。 |
| [地理位置範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 地理位置範例示範如何使用地理位置 API 來取得使用者電腦的地理位置。 應用程式可以使用地理位置 API 來取得位置一次，也可以持續追蹤位置。 |
| [訊息對話方塊範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 這個範例示範如何使用 MessageDialog 來顯示對話方塊、設定命令和其動作，以及變更預設按鈕。 `Windows.UI.Popups`命名空間包含 MessageDialog 類別。 |
| [>mediastreamsource 媒體擴充功能範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何在 Windows Store 應用程式中支援 Microsoft Silverlight >mediastreamsource 概念。 |
| [DirectWrite 垂直文字範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 這個範例會使用 DirectWrite 和 Direct2D，在自訂版面配置圖形中正確地顯示垂直文字。 |
| [DXGI 交換鏈旋轉範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 這個範例會示範 IDXGISwapChain1：： SetRotation 方法，以及如何搭配使用方法與 prerotated 內容，以改善呈現效能。 |
| [Direct2D 自訂影像效果範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何使用標準像素、頂點和計算著色器來執行自訂 Direct2D 效果。 |
| [DirectX 觸控輸入範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何在具有 Direct3D 的 c + + 應用程式中，使用觸控和滑鼠流覽3-d 環境。 |
| [XInput 遊戲控制器範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何在 c + + 應用程式中使用 XInput Api。 它會從 Xbox 遊戲控制器讀取輸入，並顯示類比杆移動和按鈕按下的相關資料。 |
| [Direct3D-Direct2D interop 範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何與 Direct2D 和 DirectWrite 交互操作，以將文字寫入至 Direct3D 轉譯目標。 它是一種有效的方法，可讓您在遊戲和3-d 應用程式中建立標題顯示和文字型 readouts，例如評分面板。 |
| [新聞訂閱範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範可從 web 服務取得摘要之 Windows 8 的基本 Windows Store 應用程式。 此範例目前以 JavaScript、c #、c + + 和 VB 程式設計語言提供。 |
| [應用程式磚和徽章範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何使用應用程式磚，也就是開始畫面中您應用程式的表示和啟動點。 它也會示範如何在該磚上使用徽章。 當應用程式未執行時，這是應用程式將狀態資訊轉送給使用者的方法。 |
| [XAML 使用者和自訂控制項範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 這個範例會示範如何建立和使用 XAML `UserControl` 專案，以及為您的專案建立自訂控制項。 |
| [Direct3D 資源載入範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何使用 DirectX 載入適用于 c + + 應用程式的 Direct3D 資源。 |
| [XAML ListView 和 GridView 自訂互動範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 這個範例會示範控制項的互動模型 `ListView` 。 |
| [XAML Web 視圖控制項範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 這個範例會示範如何使用 `WebView` 控制項來顯示 URL、載入 HTML、與中的腳本互動， `WebView` 以及使用 `WebViewBrush` 。 |
| [羅盤感應器範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何使用 `Windows.Devices.Sensors.Compass` API。 此範例可讓使用者將羅盤讀取視為磁性北部，並根據已安裝的感應器（即 true-北部值）來查看。 |
| [顯示方向範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何使用 `DisplayProperties` 類別來設定應用程式中的顯示方向。 |
| [Direct2D 插補模式範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例會顯示 Direct2D 所使用的各種插補模式。 |
| [全球化喜好設定範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 這個範例示範如何使用 `Windows.System.UserProfile.GlobalizationPreferences` 類別來取得使用者的全球化喜好設定。 它也會顯示如何使用 `GeographicRegion` 和 `Language` 類別。 |
| [Direct2D 幾何實現範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例說明多核心幾何鑲嵌如何有助於減少幾何轉譯時間。 使用不透明度遮罩和網格是傳統幾何轉譯的替代方案，在某些情況下可能更好。 |
| [語言字型對應範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 這個範例示範如何使用 `LanguageFontGroup` 命名空間中的類別，來取得特定語言的字型建議 `Windows.Globalization.Fonts` 。 |
| [傾角羅盤感應器範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例說明如何使用 `Windows.Devices.Sensors.Inclinometer` API。 此範例可讓使用者針對3軸傾角羅盤，查看 X 軸、Y 軸和 Z 軸的傾斜角度。 |
| [XAML 高對比樣式範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範在您的應用程式中執行高對比模式支援的各種技術。 高對比模式的支援非常重要，可讓具有視力問題的人員存取您的應用程式。 |
| [輸入裝置功能範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 這個範例示範如何查詢連接到使用者裝置的輸入裝置。 以及如何支援 Windows Store 應用程式的指標、觸控、畫筆/手寫筆、滑鼠和鍵盤輸入模式。 |
| [郵件用戶端的 EAS 原則範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例說明郵件用戶端如何抓取裝置資訊，以及如何使用提供的 Exchange Active Sync (EAS) 原則。 Windows Store 應用程式可以設定其郵件用戶端，以保持符合指定的 EAS 原則。 |
| [DatagramSocket 範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 這個範例會 `DatagramSocket` 使用 Windows 執行階段所提供的網路功能，來示範類別的基本概念。 範例的用戶端元件會建立 UDP 通訊端、使用通訊端來傳送和接收資料，然後關閉通訊端。 |
| [DirectWrite hello world 範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 這個範例示範如何使用 DirectWrite 和 Direct2D，將文字 "Hello World" 轉譯為 `CoreWindow` 。 |
| [壓縮範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何從檔案讀取結構化資料，並將壓縮的資料寫入至新檔案，以及如何讀取壓縮的資料並將解壓縮的資料寫入新檔案。 許多應用程式都需要壓縮和解壓縮資料。 |
| [網路狀態背景範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何使用網際網路目前的條件，為網路狀態變更事件註冊背景工作處理常式，以判斷網際網路連線設定檔中的變更。 |
| [應用程式套件資訊範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例說明如何使用 Windows 執行階段封裝 API 取得封裝資訊。 使用者將您的 Windows Store 應用程式取得為應用程式套件。 Windows 會使用應用程式套件中的資訊，以每個使用者為基礎來安裝應用程式。 |
| [LightSensor 範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例說明如何使用 `Windows.Devices.Sensors.LightSensor` API。 此範例可讓使用者以 LUX 值的形式來查看環境光源讀取。 您可以選擇下列兩種案例之一： LightSensor 資料事件、目前的光線感應器讀數等等。 |
| [行動寬頻帳戶布建範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何使用 Windows 8 行動寬頻布建代理程式 API (`Windows.Networking.NetworkOperators.ProvisioningAgent`) 來設定具有必要連線資訊和存取布建的 Windows 8。 |
| [媒體播放至範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範播放至 API。 它會說明如何擴充媒體應用程式，以將影片、音訊和影像串流至區域網路上的其他裝置。 |
| [輸入觸控鍵盤範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 這個範例示範如何在不是衍生自平臺控制項的自訂控制項中，自動啟動觸控鍵盤。 此範例會執行需要鍵盤輸入的自訂控制項，而不是衍生自標準 XAML 控制項。 |
| [XAML 動畫庫範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 這個範例示範如何建立專案的動畫，並將簡化函式套用至動畫，以達成各種效果。 |
| [ (Windows 8 的貼齊範例) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 已貼齊的狀態是四個可能的應用程式檢視狀態之一。 貼齊應用程式會將應用程式的大小調整為320圖元寬，讓它能夠與其他應用程式共用畫面。 貼齊可同時顯示兩個應用程式。 |
| [轉碼媒體範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何使用 `Windows.Media.Transcoding` API 在 Windows Store 應用程式中轉碼影片檔案。 轉碼是數位媒體檔案 (例如視訊或音訊檔案) 的轉換，也就是從一種格式變成另一種格式。 |
| [XAML 雙維度轉換範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何使用二維轉換來修改如何在您的應用程式中顯示元素。 「轉換」定義了如何將點從一個座標空間對應或轉換到另一個座標空間。 |
| [IXmlReader 和 IXmlWriter XML 資料讀取寫入範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 這個範例示範如何 `IXmlReader` `IXmlWriter` 在您的 Windows Store 應用程式中使用 c + + 來使用和。 它們是用來從一般 XML 格式的文字檔讀取和寫入 XML 資料。 這些介面是 Windows Win32 和 COM Api 的一部分，但 Windows 執行階段支援。 |
| [使用 capture 裝置範例 (Windows 8) 的媒體抓取 ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 這個範例會示範如何使用 `MediaCapture` API 從捕獲裝置（例如網路攝影機）捕獲影片、音訊和圖片。 |
| [XAML 快顯視窗範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 這個範例示範如何在您的專案中建立和使用 XAML Popup 元素。 |
| [CameraCaptureUI 範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何使用 `Windows.Media.Capture.CameraCaptureUI` API，其會顯示全螢幕 UI 來捕捉相片或影片。 相機捕獲 UI 提供可從相片切換到影片的控制項、拍攝時間延遲相片的計時器等等。 |
| [XAudio2 音訊檔案播放範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何在應用程式中使用 XAudio2。 |
| [Hilo c + + 範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何使用 c + + 和 XAML 來建立完整的 Windows Store 應用程式。 Hilo photo 範例提供 c + + 開發人員的指引，這些開發人員想要使用新式 c + +、XAML 和 Windows 執行階段來建立 Windows 8 應用程式。 |
| [DirectWrite 自訂文字轉譯器範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何針對 DirectWrite 執行自訂文字轉譯器。 |
| [DirectWrite 字型列舉範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何使用 DirectWrite，在使用者的裝置上列出系統字型集合中的字型。 |
| [Direct2D 觀點轉換範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何使用 `DrawBitmap` API 來顯示已套用透視轉換的影像。 |
| [CameraOptionsUI 範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何在裝置應用程式中使用相機選項。 `CameraOptionsUI`API 會顯示用於調整相機設定的 UI。 此範例需要網路攝影機。 |
| [XInput 音訊控制器播放範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何在應用程式中 XAudio2 播放到 XInput 裝置，例如耳機。 |
| [Direct2D 3D 轉換效果範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範在立體空間中轉換影像的不同方法。 |
| [Windows 帳戶授權範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 這個範例示範如何使用 `Windows.Security.Authentication.OnlineId` 命名空間的成員，以委派模式的 Microsoft 帳戶來驗證使用者。 以及如何使用 REST 通訊協定，將取得的權杖傳送到 Live Connect Api。 |
| [數位格式設定和剖析範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 這個範例示範如何 `DecimalFormatter` `CurrencyFormatter` `PercentFormatter` `PermilleFormatter` 在命名空間中使用、、和類別 `Windows.Globalization.NumberFormatting` 。 它們是用來顯示和剖析數位、貨幣和百分比值。 |
| [DXGI 提供和回收資源範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何 `IDXGIDevice2::OfferResources` `IDXGIDevice2::ReclaimResources` 在 c + + 應用程式中搭配 DIRECTX 使用 DXGI 和 api。 |
| [Web 驗證 broker 範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範 web authentication broker WinRT API。 它可讓您針對 OAuth 提供者（例如 Facebook、Google、Microsoft 和 Twitter）啟用單一登入 (SSO) 連接。 |
| [XAudio2 音訊串流效果範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何使用 XAudio2 和媒體基礎 Api 在 c + + 應用程式中進行音訊串流。 |
| [啟動顯示畫面範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何模擬 Windows 針對您的應用程式顯示的啟動顯示畫面，方法是在 Windows 關閉顯示的啟動顯示畫面時，正確定位類似的影像。 |
| [SMS 背景工作範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例說明如何使用 Windows 8 行動寬頻簡訊 API (`Windows.Devices.Sms`) 與背景工作 API (， `Windows.ApplicationModel.Background` 以傳送和接收 SMS 文字訊息。 |
| [SMS 訊息傳送、接收和 SIM 管理範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例說明如何使用 Windows 8 行動寬頻簡訊 API (`Windows.Devices.Sms`) 。 |
| [試用應用程式和應用程式內購買範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何使用 Windows 市集中提供的授權 API 來判斷應用程式的授權狀態，或應用程式內購買所啟用的功能。 |
| [輸入觸控鍵盤文字輸入範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何在觸控鍵盤上啟用優化的視圖。 它的運作方式是將輸入範圍和輸入類型與命名空間中的控制項搭配使用 `WinJS.UI` ，以及搭配 `TextBox` 和 `RichEdit` XAML 控制項使用。 |
| [XAML 文字編輯範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何在您的應用程式中使用文字輸入控制項。 |
| [執行緒集區範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例說明如何使用 Windows 執行階段執行緒集區 API，以非同步方式執行工作專案。 |
| [消費者介面自動化核心視窗提供者範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 這個範例示範如何建立 Microsoft 消費者介面自動化提供者。 它會將 Windows Store 應用程式的程式設計資訊提供給可存取的技術（例如螢幕讀取器）。 此範例是 Direct2D 應用程式。 |
| [XAML 協助工具範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例說明如何將基本協助工具支援新增至您的應用程式。 |
| [播放清單範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 這個範例示範如何建立、儲存、顯示和編輯音訊檔案的播放清單。 這個範例會使用命名空間中的類別 `Windows.Media.Playlists` 。 |
| [媒體伺服器用戶端範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何使用媒體伺服器 API 建立媒體伺服器用戶端。 媒體伺服器範例示範如何在您的區域網路上以程式設計方式流覽數位媒體伺服器，並顯示其所有的影片檔案。 |
| [Direct2D 雜誌應用程式範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何使用 Direct2D、DirectWrite、Windows 影像處理元件 (WIC) 和 XAML 來建立具有雜誌類型簡報的應用程式。 |
| [行動寬頻帳戶和裝置管理範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何使用行動 `Windows.Networking.NetworkOperators` 網路操作員 (MNO) 所採用的 Windows 8 Mobile 寬頻 API () 。 它會示範如何使用 MobileBroadbandAccount Api 來取出並顯示可用的行動寬頻帳戶。 |
| [鄰近性範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 這個範例示範如何使用 `PeerFinder` 和 `ProximityDevice` 類別來與附近的電腦通訊。 您可以使用 `Proximity` API 在點一下手勢中交換小型訊息，或設定對等應用程式之間的通訊端連線。 |
| [建立 Windows 執行階段同進程元件範例 (C + + CX)  (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 這個範例示範如何在 c + +/cx、JavaScript 和 c # 用戶端程式代碼中使用 c + +/CX 建立元件。 OvenServer 專案包含名為的執行時間類別 `Oven` ，它會實 `IOven` 介面和 `IAppliance` 介面。 |
| [裝置自動輪替喜好設定範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例說明如何使用 `DisplayProperties` 類別來處理和驗證裝置旋轉事件。 |
| [即時通訊範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何使用低延遲功能來啟用即時通訊應用程式。 |
| [ (Windows 8) 共用內容來源應用程式範例 ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 這個範例會示範應用程式如何與另一個應用程式共用內容。 此範例會使用來自 `Windows.ApplicationModel.DataTransfer` 命名空間的類別。 |
| [搜尋合約範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何讓使用者在選取搜尋快速鍵並開啟 [搜尋] 窗格時，搜尋您的應用程式。 以及如何使用 [搜尋] 窗格來顯示使用者查詢的建議。 |
| [原始通知範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何使用原始通知，這是沒有任何相關聯的 UI 可執行應用程式背景工作的推播通知。 |
| [Direct2D 基本影像效果範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 這個範例示範如何載入影像、對它套用高斯模糊效果，然後將它顯示在中 `Windows::UI::Core::CoreWindow` 。 |
| [基本範例 (Windows 8 的 Direct2D 效果) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例說明如何將影像效果套用至 Direct2D 基本專案。 這個範例會使用 Direct2D 繪製圓角矩形，然後在矩形的中間繪製 DirectWrite 的文字。 然後，它會對它套用效果圖形。 |
| [ControlChannelTrigger StreamSocket 範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例會示範如何 `ControlChannelTrigger` 在 Windows Store 應用程式中使用類別。 它會使用 TCP `StreamSocket` ，因此應用程式一律會連線且一律可連線。 此範例示範如何使用背景網路通知。 |
| [ControlChannelTrigger StreamWebSocket 範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何使用 `ControlChannelTrigger` 類別，讓使用 StreamWebSocket 的 Windows Store 應用程式一律保持連線且一律可連線。 此範例示範如何使用背景網路通知。 |
| [關聯啟動範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例說明如何針對檔案類型或通訊協定啟動使用者的預設應用程式。 您也可以瞭解如何讓您的應用程式成為檔案類型或通訊協定的預設應用程式。 |
| [AtomPub 範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何從 web 存取、建立、更新及移除新聞訂閱內容摘要。 它使用 Atom 發行標準的 Windows 執行階段執行。 |
| [憑證註冊範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何在證書階層中建立和註冊憑證。 若要取得 Windows 8 的評估版本，請移至 Windows 8。 若要取得 Microsoft Visual Studio 2012 的評估版本，請移至 Visual Studio 2012。 |
| [剪貼簿應用程式範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 這個範例會示範應用程式如何使用剪貼簿命令，包括複製、貼上、剪下和移動。 此範例會使用來自 `Windows.ApplicationModel.DataTransfer` 命名空間的類別。 |
| [Direct2D 複合效果模式範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 這個範例會顯示 Direct2D 中可用的各種複合和 blend 模式範圍。 |
| [Direct3D 凹凸對應範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 這個範例會示範如何使用一般地圖和每圖元光源來進行「凹凸對應」。 |
| [行事曆詳細資料和數學範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 這個範例會示範如何使用 `Calendar` 命名空間中的類別， `Windows.Globalization` 根據行事曆系統和使用者的全球化喜好設定來操作和處理日期。 |
| [裝置列舉範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例說明如何使用裝置列舉 API 來尋找可用的裝置，並尋找裝置資訊。 此範例顯示兩個案例：在第一個案例中，會使用裝置列舉 API 來尋找特定的裝置介面。 |
| [DirectWrite 段落文字範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 這個範例示範如何使用 DirectWrite 和 Direct2D，將段落文字轉譯為 `CoreWindow` 。 然後，將對齊方式和字元間距套用至版面配置。 |
| [回應螢幕小鍵盤範例的外觀 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | [此檔是初稿，隨時可能變更。]這個範例會示範如何接聽和回應螢幕上螢幕鍵盤的外觀。 將焦點提供給需要在沒有鍵盤的裝置上輸入文字的元素時。 |
| [XAML 資料系結範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 這個範例會示範使用系結類別和系結標記延伸的基本資料系結技術。 |
| [Direct3D 教學課程範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例為五課的教學課程。 它提供了 Direct3D API 的簡介，並介紹許多其他 DirectX 範例中所使用的概念和程式碼。 |
| [Direct2D 會影響相片調整應用程式範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例顯示使用 Direct2D 效果的各種常見相片操作技術。 此範例分為數個部分。 第1課：顯示使用 Direct2D 效果載入和繪製影像的基本概念。 |
| [Windows 音訊會話 (WASAPI) 範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 示範如何使用 Windows 音訊會話 API (WASAPI) 來進行各種音訊相關工作。 |
| [使用者功能變數名稱範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 這個範例會示範由命名空間的類別所提供的網域相關功能 `UserInformation` `Windows.System.UserProfile` 。 UserInformation 類別可讓應用程式取得和設定使用者的相關資訊。 |
| [USSD 訊息管理範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何使用 USSD 通訊協定搭配支援 GSM 的行動寬頻裝置來管理網路帳戶。 USSD 通常是由行動網路操作員 (MNO) 的行動寬頻設定檔帳戶管理所使用。 |
| [Bing 地圖服務路線優化程式範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何使用 JavaScript 和 Visual C++，以及建立名為 Bing 地圖服務路線優化程式 Windows 8 的應用程式。 Bing 地圖服務路線優化程式會使用 JavaScript 來平行定義 UI 和 c + +，以進行計算昂貴的演算法。 |
| [Direct2D 和 DirectWrite 路徑範例 (Windows 8) 的動畫文字 ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 這個範例示範如何使用 Direct2D 和 DirectWrite，沿著動畫、非線性幾何路徑呈現文字字串。 應用程式呈現 "Hello，World！" 在貝茲曲線上重複數次不同的語言。 |
| [Wi-fi 熱點驗證範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何使用 Windows 8 Mobile 寬頻 API (`Windows.Networking.NetworkOperators`) 進行 wi-fi 熱點驗證。 您可以使用此機制作為設定 Wi-fi 熱點之靜態認證的替代方案。 |
| [XAML 影像範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範各種使用 Image 控制項和 BitmapImage 類別在應用程式中顯示和操作影像的技巧。 |
| [家庭 (Windows 8) 的家庭應用程式範例 ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 這個範例示範如何使用 `HomeGroup` 來開啟、搜尋和共用檔案。 這個範例會使用 `HomeGroup` 在和中找到的一些 `Windows.Storage.Pickers` 選項 `Windows.Storage.KnownFolders` 。 |
| [UI 對比和設定範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例說明如何在基本 c # 或 JavaScript 應用程式中使用 UI 設定 Api。 |
| [資料夾列舉範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何列出位置內的最上層檔案和資料夾。  (例如，資料夾、裝置或網路位置。 ) 和，如何使用查詢來列出位置中的所有檔案，方法是將它們排序成檔案群組。 |
| [檔案選擇器範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何藉由讓使用者透過檔案選擇器選擇檔案和資料夾來存取檔案和資料夾。 以及如何儲存檔案，讓使用者可以指定要儲存的檔案名、檔案類型和位置。 |
| [檔案選擇器合約範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 這個範例會示範應用程式如何透過檔案選擇器，將檔案、儲存位置，以及即時檔案更新提供給其他應用程式。 它是藉由參與檔案開啟選擇器協定、檔案儲存選擇器協定和快取檔案更新程式協定來完成。 |
| [程式設計檔搜尋範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何查詢資料夾、媒體櫃、裝置或網路位置等位置中的檔案。 它會使用 `Windows.Storage.Search` API。 此範例中的重要 Api 包括： `QueryOptions` 類別、 `StorageFileQueryResult` 類別和其他專案。 |
| [檔案和資料夾縮圖範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何取出檔案和資料夾的縮圖。 它會使用 `Windows.Storage.FileProperties` API。 |
| [輸入操作和手勢 (c + +) 範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何 `GestureRecognizer` 使用 c + + 和 DirectX，在 Windows Store 應用程式中處理 api 的指標輸入和處理操作和筆勢。 |
| [Direct3D HLSL 碎形產生器範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何使用 Direct3D HLSL 和 DirectCompute 計算著色器來建立碎形映射。 |
| [XAML Direct2D 光源效果範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範 Direct2D 效果中可用的光源效果。 光源效果屬性是由 XAML 介面控制項控制，然後透過 XAML SwapChainBackgroundPanel 使用 Direct2D 來顯示。 |
| [Direct2Dapp 列印範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何將 Direct2D 列印支援新增至 Windows Store 應用程式。 此範例示範如何使用 Direct2D 功能來呈現 Windows Store 應用程式的內容，以進行列印。 以及如何將轉譯的內容傳送至印表機。 |
| [Direct2D 列印影像和效果範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何在 Windows Store 應用程式中列印 Direct2D 影像和 Direct2D 效果。 |
| [Direct2D 動畫文字範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 這個範例會示範如何使用 Direct2D 方法來快速呈現文字 `FillOpacityMask` 。 此範例也會回應觸控。 雙手指縮小可以用來放大和縮小文字。 |
| [Direct3D 後續處理效果範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 這個範例示範如何在簡單的旋轉 cube 場景上，使用向下調整的中繼緩衝區來進行 Direct3D 11.1 後置處理。 |
| [擴充的語言服務 (ELS) 範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何在 Windows Store 應用程式中使用擴充語言服務 (ELS) 。 此範例會示範如何使用三個可用的 ELS 服務的案例。 這些案例會示範如何要求特定的服務。 |
| [DirectWrite 點擊測試範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例顯示如何使用 DirectWrite 的點擊測試功能。 它們是用來判斷所顯示文字的哪個部分要被點擊或觸及。 |
| [DirectWrite (Windows 8) 的内嵌物件範例 ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何將内嵌物件插入至文字配置，例如影像。 |
| [以 XAML 向量為基礎的繪圖範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何在您的應用程式中繪製以向量為基礎的圖形。 |
| [藍牙呼叫控制範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 藍牙 CallControl 範例會示範如何設定預設的藍牙通訊裝置來處理呼叫。 此範例有 JavaScript、c #、c + + 和 VB.Net 版本。 此範例需要 Windows 事件和事件處理的知識。 |
| [Direct2D 命令清單範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何使用命令清單。 它是用來記錄一組向量命令、從命令清單建立影像筆刷，然後用它來填滿矩形幾何。 命令清單會保留向量的解析獨立性。 |
| [ControlChannelTrigger XMLHTTPRequest 範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何使用 `ControlChannelTrigger` 類別，讓使用的 Windows Store 應用程式 `IXMLHTTPRequest2` 一律保持連線且一律可連線。 此範例示範如何在 Windows Store 應用程式中使用背景網路通知。 |
| [XInput 和 JavaScript 控制器草圖範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何將 XInput c + + API 包裝在 Windows 執行階段元件中。 然後，它會從使用 JavaScript 的 Windows Store 應用程式呼叫它。 此範例會執行一個草圖應用程式，可讓您使用 Xbox 遊戲控制器來選取線條粗細及更多。 |
| [Direct2D >convolve 矩陣效果範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範 >convolve 矩陣效果的 Direct2D 效果。 此範例中有一些範例卷積核心矩陣：傳遞 (無 op) 、方塊模糊 (寬度 5) 、簡單邊緣偵測、簡單的銳化、浮凸、垂直斑點 (高度 10) 上述等等。 |
| [DirectX 交換鏈執行範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何 `CoreWindow` 在原生應用程式中接收事件，以及如何將 DirectX 交換鏈連接至應用程式視圖。 |
| [認證選擇器範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何使用 `Windows.Security.Credentials.UI.CredentialPicker` 類別來取得認證。 這些認證可以傳遞給需要它們的 Api，例如 `HttpClient` 。 |
| [Direct2D 動畫範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 這個範例示範如何使用 Direct2D，沿著螺旋線路徑呈現 Direct2D 基本型別和製作動畫。 |
| [共用內容目標應用程式範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 這個範例會示範應用程式如何接收從其他應用程式共用的內容。 這個範例會使用 `Windows.ApplicationModel.DataTransfer` 和命名空間中的類別 `Windows.ApplicationModel.DataTransfer.Share` 。 |
| [Direct2D 儲存至影像檔案範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何使用 Direct2D 和 DirectWrite 轉譯至螢幕。 以及如何使用 WIC API 將轉譯的影像儲存至磁片。 |
| [根據 DPI 範例 (Windows 8) 進行調整 ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例說明如何建立可根據螢幕的圖元密度進行調整的應用程式。 它會載入適當規模的影像，或覆寫預設調整。 此範例會使用 `Windows.Graphics.Display` API。 |
| [建立 Windows 執行階段同進程元件範例 (c # )  (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何在 c # 中建立用於 c + +/CX、JavaScript 和 c # 用戶端程式代碼的元件。 OvenServer 專案包含名為的執行時間類別 `Oven` ，它會實 `IOven` 介面和 `IAppliance` 介面。 |
| [推播和定期通知用戶端範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例說明用戶端應用程式如何註冊及接聽從 web 伺服器傳送的推播通知。 您可以使用推播通知來更新徽章或磚、引發快顯通知，或啟動背景工作。 |
| [可攜式裝置 API 範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例說明如何 `IPortableDevice` 從 c + + 應用程式存取 COM API。 若要瞭解如何 `IPortableDevice` 從 Desktop c + + 應用程式存取 COM api，請參閱可攜式裝置 COM Api 範例。 |
| [PlayToReceiver 範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 這個範例示範如何建立軟體播放至接收者。 若要通告軟體播放至接收者，請按一下 [啟動接收者] 按鈕。 若要停止接收者，請按一下 [停止接收者] 按鈕。 |
| [鎖定螢幕個人化範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何使用 `LockScreen` API 來設定目前使用者的鎖定畫面影像。 此範例會使用來自 `Windows.System.UserProfile` 命名空間的類別。 |
| [認證保險箱範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何使用 WinRT `PasswordVault` api，以及如何使用認證保險箱來儲存 web 認證。 特定案例包括具有單一資源的單一使用者，以及具有單一資源的多個使用者。 |
| [媒體引擎原生 c + + 影片播放範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何 `MediaEngine` 在原生 c + + 應用程式中使用 API 播放影片。 |
| [媒體擴充功能範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 這個範例示範如何使用媒體擴充功能。 您可以使用配置處理常式，將效果套用至影片、解碼影片，以及建立媒體串流。 |
| [鎖定畫面應用程式範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例會顯示應用程式如何在鎖定畫面上顯示（當電腦鎖定時顯示的畫面），以及提供基本狀態資訊的徽章或磚來提供更詳細的狀態。 |
| [XAML 文字顯示範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何控制應用程式中的文字外觀。 |
| [SimpleOrientationSensor 範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例說明如何使用 `Windows.Devices.Sensors.SimpleOrientationSensor` API。 |
| [Direct3D sprite 範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 這個範例會提供 sprite 批次行為的 Direct3D 執行，類似于「範本」 `SpriteBatch` API。 Sprite 是可在立體場景中獨立轉換和管理的2D 點陣圖，通常用於2D 遊戲中。 |
| [Direct3D stereoscopic 3D 範例 (Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何使用 Direct3D 將 stereoscopic 立體效果新增至 c + + 應用程式。 它也會示範如何在 Direct3D 中回應系統的身歷聲變更。 Stereoscopic 3-d 效果需要可支援身歷聲3D 的顯示器。 |
| [使用 c + + 範例 (建立 Windows 執行階段 DLL 元件 Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例說明如何在 Microsoft Visual C++ 中建立同進程 DLL 元件。 它是在 c + +/CX、JavaScript 和 c # 用戶端程式代碼中使用。 OvenServer 專案包含名為的執行時間類別 `Oven` ，它會實作為 `IOven` 介面。 |
| [使用 c + + 範例 (建立 Windows 執行階段 EXE 元件 Windows 8) ](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 這個範例示範如何在 Microsoft Visual C++ 中建立跨進程的 EXE 元件。 它是在 c + +/CX、JavaScript 和 c # 用戶端程式代碼中使用。 OvenServer 專案包含名為的執行時間類別 `Oven` ，它會實作為 `IOven` 介面。 |
