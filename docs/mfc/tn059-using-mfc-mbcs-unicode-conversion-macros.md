---
title: "TN059：使用 MFC MBCS/Unicode 轉換巨集 | Microsoft Docs"
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
  - "vc.mfc.mbcs"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "轉換巨集 [C++]"
  - "轉換 Unicode"
  - "巨集 [C++], MBCS 轉換巨集"
  - "MBCS [C++], 轉換巨集"
  - "MFCANS32.DLL"
  - "TN059"
  - "Unicode [C++], 轉換巨集"
  - "Unicode [C++], OLE 介面"
ms.assetid: a2aab748-94d0-4e2f-8447-3bd07112a705
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN059：使用 MFC MBCS/Unicode 轉換巨集
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  下列技術提示自其納入線上文件以來，未曾更新。  因此，有些程序和主題可能已過期或不正確。  如需最新資訊，建議您在線上文件索引中搜尋相關的主題。  
  
 這個摘要會描述如何針對 MBCS\/Unicode 使用在 AFXPRIV.H. 定義的巨集轉換。  如果您的應用程式直接處理 OLE 應用程式開發介面或基於某些原因，常常需要於 Unicode 和 MBCS 之間轉換，這些巨集是最有用的。  
  
## 概觀  
 在 MFC 3.x，當呼叫 OLE 介面時，一個特別的 DLL \(MFCANS32.DLL\) 用於在 Unicode 和 MBCS 之間自動轉換。  如果 OLE API 和介面為 MBCS，即使它們永遠都是 Unicode \(除了在 Macintosh\)，這個 DLL 是允許撰寫 OLE 應用程式的幾乎透明的層級。  雖然這個層級很方便且可讓應用程式從 Win16 快速移植到 Win32 \(MFC、Microsoft Word、Microsoft Excel 和 VBA，是使用這個技術的某些 Microsoft 應用程式\) 時，它有時會影響效能。  因此， MFC 4.x 不使用這個 DLL 而直接與 Unicode OLE 介面溝通。  為了這樣做，當呼叫 OLE 介面時 MFC 需要轉換成 Unicode 到 MBCS，且當實作 OLE 介面時通常需要從 Unicode 轉換為 MBCS。  為了方便有效地修改與處理，建立許多巨集使這個轉換更加容易。  
  
 其中一個創造這類巨集的最大阻礙是記憶體配置。  由於字串無法立刻的轉換，必須配置新記憶體以保留轉換結果。  這可以與下列程式碼達成類似的功能:  
  
```  
// we want to convert an MBCS string in lpszA  
int nLen = MultiByteToWideChar(CP_ACP, 0,lpszA, -1, NULL, NULL);  
LPWSTR lpszW = new WCHAR[nLen];  
MultiByteToWideChar(CP_ACP, 0,   
   lpszA, -1, lpszW, nLen);  
// use it to call OLE here  
pI->SomeFunctionThatNeedsUnicode(lpszW);  
// free the string  
delete[] lpszW;  
```  
  
 這個方法產生了一些問題。  主要問題是需要撰寫，偵錯及測試大量的程式碼。  從前是簡單的函式呼叫的事，現在變得更為複雜。  此外，這樣做有造成執行階段的重大額外負荷。  每次完成轉換，記憶體堆積必須配置和釋放。  最後，上述程式碼需要為了 Unicode 和 Macintosh 組建加入適當的 `#ifdefs` \(這些不需要這項轉換\) 。  
  
 我們想出的解決方案為建立 1\) 掩蓋各種平台之間的差異 2\) 使用一個有效的記憶體配置方案及 3\) 可以簡單插入現有的原始程式碼的某些巨集。  這是其中一個定義的範例:  
  
```  
#define A2W(lpa) (\  
    ((LPCSTR)lpa == NULL) ? NULL : (\  
          _convert = (strnlen(lpa)+1),\  
        AfxA2WHelper((LPWSTR) alloca(_convert*2),   
      lpa, _convert)\  
    )\  
)  
```  
  
 使用這個巨集而不是上述程式碼讓事情簡單化:  
  
```  
// use it to call OLE here  
USES_CONVERSION;  
pI->SomeFunctionThatNeedsUnicode(T2OLE(lpszA));  
```  
  
 會因轉換而產生額外呼叫，不過，使用巨集是簡單且有效的。  
  
 每一個巨集的實作使用 \_alloca\(\) 函式從堆疊中配置記憶體而不是堆積。  從堆疊配置記憶體會比在堆積上配置記憶體更加快速，而且當函式結束時記憶體自動釋放。  此外，巨集避免呼叫 **MultiByteToWideChar** \(或 **WideCharToMultiByte**\) 超過一次。  這個由配置比必要的更多一點的記憶體完成。  我們知道 MBC 會轉換為最多一個 **WCHAR** ，並針對每個 **WCHAR** 我們將有最多兩個 MBC 位元組。  藉由配置多於必要的數量，不過，這永遠足夠處理轉換使得這能避免第二次呼叫轉換函式。  對 Helper 函式 **AfxA2Whelper** 的呼叫減少必須完成才能執行轉換的引數推入的數目 \(這會比直接呼叫 **MultiByteToWideChar** 產生較小的程式碼 \)。  
  
 為了要讓巨集具有儲存暫存長度的空間，宣告名為 \_convert 的區域變數讓使用轉換巨集的每個函式執行這個是必要的。  這個由叫用 **USES\_CONVERSION** 巨集完成，如上例範例中所述。  
  
 有泛型轉換巨集和 OLE 特定巨集。  這兩個不同的巨集會於下面討論。  所有巨集位於 AFXPRIV.H。  
  
## 泛型轉換巨集  
 泛型轉換巨集形成這個的基本機制。  前一章節的巨集範例和實作，A2W，是一種這類的泛型巨集。  它不會特別與 OLE 相關。  一組泛型巨集如下所列:  
  
```  
A2CW      (LPCSTR) -> (LPCWSTR)  
A2W      (LPCSTR) -> (LPWSTR)  
W2CA      (LPCWSTR) -> (LPCSTR)  
W2A      (LPCWSTR) -> (LPSTR)  
```  
  
 除了轉換文字以外，也有巨集和 Helper 函式進行轉換 `TEXTMETRIC`、 `DEVMODE`、 `BSTR` 和 OLE 配置的字串。  這些巨集超出這個討論範圍–請參閱 AFXPRIV.H 取得關於這些巨集的詳細資訊。  
  
## OLE 轉換巨集  
 OLE 轉換巨集對預期處理 **OLESTR** 字元的函式所設計。  如果檢查 OLE 標頭，您將看到 **LPCOLESTR** 和 **OLECHAR**的許多參考。  這些型別用來以並非專屬於平台的方法參考用於 OLE 介面的字元類型。  **OLECHAR** 對應至 Win16 的 `char` 和 Macintosh 平台和 Win32 的 **WCHAR** 。  
  
 為了保持MFC 程式碼中 **\#ifdef** 的指示詞數到最低，我們有對包含 OLE 字串的每個轉換設計類似的巨集。  以下巨集最為常用：  
  
```  
T2COLE   (LPCTSTR) -> (LPCOLESTR)  
T2OLE   (LPCTSTR) -> (LPOLESTR)  
OLE2CT   (LPCOLESTR) -> (LPCTSTR)  
OLE2T   (LPCOLESTR) -> (LPCSTR)  
```  
  
 同樣地，有執行 `TEXTMETRIC`、 `DEVMODE`、 `BSTR`和 OLE 配置字串的相似巨集。  如需詳細資訊，請參考 AFXPRIV.H。  
  
## 其他考量  
 不要在緊密迴圈使用巨集。  例如，您不要撰寫下列程式碼:  
  
```  
void BadIterateCode(LPCTSTR lpsz)  
{  
   USES_CONVERSION;  
   for (int ii = 0; ii < 10000; ii++)  
      pI->SomeMethod(ii, T2COLE(lpsz));  
}  
```  
  
 上述程式碼可能會根據字串 `lpsz` 的內容造成配置數 MB 的記憶體於堆疊上\!  這也需要時間轉換每個迴圈的每個反覆中項目的字串。  相反地，請移動這類常數轉換在迴圈外:  
  
```  
void MuchBetterIterateCode(LPCTSTR lpsz)  
{  
   USES_CONVERSION;  
   LPCOLESTR lpszT = T2COLE(lpsz);  
   for (int ii = 0; ii < 10000; ii++)  
      pI->SomeMethod(ii, lpszT);  
}  
```  
  
 如果字串不是常數，則請封裝方法呼叫為函式。  這將允許每次轉換緩衝區都會被釋放。  例如：  
  
```  
void CallSomeMethod(int ii, LPCTSTR lpsz)  
{  
   USES_CONVERSION;  
   pI->SomeMethod(ii, T2COLE(lpsz));  
}  
  
void MuchBetterIterateCode2(LPCTSTR* lpszArray)  
{  
   for (int ii = 0; ii < 10000; ii++)  
      CallSomeMethod(ii, lpszArray[ii]);  
}  
```  
  
 不要傳回其中一個巨集的結果，除非傳回值意味著會在傳回之前製作資料拷貝。  例如，以下這個程式碼是不好的：  
  
```  
LPTSTR BadConvert(ISomeInterface* pI)  
{  
   USES_CONVERSION;  
   LPOLESTR lpsz = NULL;  
   pI->GetFileName(&lpsz);  
   LPTSTR lpszT = OLE2T(lpsz);  
   CoMemFree(lpsz);  
   return lpszT; // bad! returning alloca memory  
}  
```  
  
 上述程式碼可以藉由變更傳回值為複製的值修改:  
  
```  
CString BetterConvert(ISomeInterface* pI)  
{  
   USES_CONVERSION;  
   LPOLESTR lpsz = NULL;  
   pI->GetFileName(&lpsz);  
   LPTSTR lpszT = OLE2T(lpsz);  
   CoMemFree(lpsz);  
   return lpszT; // CString makes copy  
}  
```  
  
 巨集容易使用且容易插入至程式碼，但是對於上面警告，當使用項目時，您必須小心。  
  
## 請參閱  
 [依編號顯示的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)