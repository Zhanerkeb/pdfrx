# 0.4.36

- Introduces PdfJsConfiguration to configure pdf.js download URLs

# 0.4.35

- Download cache mechanism update (#57/#58)

# 0.4.34

- Document update

# 0.4.33

- Document update

# 0.4.32

- Add PdfViewerParams.calculateInitialPageNumber to calculate the initial page number dynamically
- Add PdfViewerParams.onViewerReady to know when the viewer gets ready

# 0.4.31

- Remove explicit CMake version spec 3.18.1

# 0.4.30

- FIXED: Link URI contains null-terminator
- Add support text/links on rotated pages
- Stability updates for PdfTextSearcher
- README.md/example updates
- Revival of PdfViewer.data/PdfViewer.custom

# 0.4.29

- Minor fixes to PdfTextSearcher

# 0.4.28

- README.md/example updates

# 0.4.27

- Minor updates and README.md updates

# 0.4.26

- Introduces PdfTextSearcher that helps you to implement search UI feature (#47)
- Example code is vastly changed to explain more about the widget functions

# 0.4.25

- FIXED: Able to scroll outside document area

# 0.4.24

- Huge refactoring on PdfViewerController; it's no longer TransformationController but just a `ValueListenable<Matrix4>`
  - This fixes an "Unhandled Exception: Null check operator used on a null value" on widget state disposal (#46)

# 0.4.23

- Introduces PdfDocumentViewBuilder/PdfPageView widgets
- Example code is super updated with index and thumbnails.

# 0.4.22

- Web: Now pdf.js is loaded automatically and no modification to index.html is required!
- Default implementation for PdfViewerParams.errorBannerBuilder to show internally thrown errors
- PdfPasswordException is introduced to notify password error
- PdfDocumentRef now has stackTrace for error
- PdfFileCache now uses dedicated http.Client instance

## 0.4.21

- Now PdfDocumentRef has const constructor and PdfViewer.documentRef is also const

## 0.4.20

- Removes PdfDocumentProvider (Actually PdfDocumentRef does everything)
- Fixes breakage introduced by 0.4.18

## 0.4.19

- firstAttemptByEmptyPassword should be true by default

## 0.4.18

- PdfDocumentProvider supercedes PdfDocumentStore (PR #42)
- pdfium 6259 for Windows, Linux, and Android
- FIXED: Bug: Tests fail due to null operator check on PdfViewerController #44

## 0.4.17

- Additional fixes to text selection mechanism

## 0.4.16

- Remove password parameters; use passwordProvider instead.
- Fixes several resource leak scenarios on PdfDocument open failures
- Restrict text selection if PDF permission does not allow copying
- Remove PdfViewer.documentRef; unnamed constructor is enough for the purpose

## 0.4.15

- Introduces PdfViewer.documentRef (#36)
- FIXED: PdfViewer.uri is broken on web for non relative paths #37
- FIXED: Don't Animate to initialPage #39

## 0.4.14

- Introduces PdfViewerParams.onDocumentChanged event
- Introduces PdfDocument.loadOutline to load outline (a.k.a. bookmark)

## 0.4.13

- Improves document password handling by async PasswordProvider (#20)
- Introduces PdfViewerParams.errorBannerBuilder

## 0.4.12

- Introduces PdfViewerParams.maxImageBytesCachedOnMemory, which restricts the maximum cache memory consumption
  - Better than logic based on maxThumbCacheCount
- Remove the following parameters from PdfViewerParams:
  - maxThumbCacheCount
  - maxRealSizeImageCount
  - enableRealSizeRendering

## 0.4.11

- Add support for PDF Destination (Page links)

## 0.4.10

- FIXED: isEncrypted property of document returns always true even the document is not encrypted (#29)

## 0.4.9

- FIXED: SelectionArea makes Web version almost unusable (#31)

## 0.4.8

- FIXED: Unhandled Exception: type 'Null' is not a subtype of type 'PdfPageRenderCancellationTokenPdfium' in type cast (#26)

## 0.4.7

- FIXED: Android build broken? Cannot find libpdfium.so error (#25)
- PdfViewerParams.loadingBannerBuilder to customize HTTP download progress
- PdfViewerParams.linkWidgetBuilder to support embedded links
- WIP: Updated text selection mechanism, which is faster and stable but still certain issues
  - Pan-to-scroll does not work on Desktop/Web
  - Selection does not work as expected on mobile devices
- Support Linux running on arm64 Raspberry PI (#23/#24)

## 0.4.6

- Introduces PdfPage.render cancellation mechanism
  - PdfPageRenderCancellationToken to cancel the rendering process
  - BREAKING CHANGE: PdfPage.render may return null if the rendering process is canceled
- PdfPageRender.render limits render resolution up to 300-dpi unless you use getPageRenderingScale
  - Even with the restriction, image size may get large and you'd better implement getPageRenderingScale to restrict such large image rendering
- PdfViewerParams default changes:
  - scrollByMouseWheel default is 0.2
  - maxRealSizeImageCount default is 3
- PdfViewerParams.scrollByArrowKey to enable keyboard navigation

## 0.4.5

- PdfViewerParams updates
  - PdfViewerParams.onPageChanged replaces onPageChanged parameter on PdfViewer factories
  - PdfViewerParams.pageAnchor replaces anchor parameter on PdfViewer factories
- pdfDocumentFromUri/PdfFileCache improves mechanism to cache downloaded PDF file
  - ETag check to invalidate the existing cache
  - Better downloaded region handling

## 0.4.4

- PdfPage.render can render Annotations and FORMS
- PdfFileCache: More realistic file cache mechanism
- Introduces PasswordProvider to repeatedly test passwords (only API layer)

## 0.4.3

- FIXED: cache mechanism is apparently broken (#12)

## 0.4.2

- PdfViewerParams.pageOverlayBuilder to customize PDF page (#17)
- Updating README.md

## 0.4.1

- Add PdfViewerParams.enableRenderAnnotations to enable annotations on rendering (#18,#19)

## 0.4.0

- Many breaking changes but they improve the code integrity:
  - PdfDocument.pages supersedes PdfDocument.getPage
  - PdfDocument.pageCount is removed
  - PdfViewerParams.devicePixelRatioOverride is removed; use getPageRenderingScale instead
- Add PdfPageAnchor.all
- PdfViewerParams.viewerOverlayBuilder/PdfViewerScrollThumb to support scroll thumbs

## 0.3.6

- PageLayout -> PdfPageLayout

## 0.3.5

- PageLayout class change to ease page layout customization
  - Add example use case in API document

## 0.3.4

- Rewriting page rendering code
  - Due to the internal structure change, page drawing customization parameters are once removed:
    - pageDecoration
    - pageOverlaysBuilder
- Example code does not enables enableTextSelection; it's still too experimental...

## 0.3.3

- FIXED: Downloading of small PDF file causes internal loading error

## 0.3.2

- Support mouse-wheel-to-scroll on Desktop platforms

## 0.3.1

- Minor API changes
- Internal integrity updates that controls the viewer behaviors
- FIX: example code does not have android.permission.INTERNET on AndroidManifest.xml
- PdfViewerParams.devicePixelRatioOverride is deprecated and introduces PdfViewerParams.getPageRenderingScale

## 0.3.0

- Many renaming of the APIs that potentially breaks existing apps

## 0.2.4

- Now uses plugin_ffi. (Not containing any Flutter plugin stab)

## 0.2.3

- Fixed: #6 PdfPageWeb.render behavior is different from PdfPagePdfium.render

## 0.2.2

- Explicitly specify Flutter 3.16/Dart 3.2 as NativeCallable.listener does not accept non-static function (#5)

## 0.2.1

- Stabilizing API surface
  - Introducing PdfViewer.asset/file/uri/custom
  - PdfViewer has documentLoader to accept function to load PdfDocument
- Fixes minor issues on PdfViewer

## 0.2.0

- Introducing PdfDocument.openUri/PdfFileCache\* classes
- Introducing PdfPermissions
- PdfPage.loadText/PdfPageText for text extraction
- Android NDK CMake to 3.18.1

## 0.1.1

- Document updates
- pdf.js 3.11.174

## 0.1.0

- First release (Documentation is not yet ready)
