# zmk-config-moNa2-v2_custom/CMakeLists.txt の最終修正案

# カスタムモジュールとして定義
zephyr_library()

# west.yml で定義したモジュール名 'zmk-pmw3610-driver' をパスとして取得
set(PMW3610_MODULE_DIR "${ZEPHYR_BASE}/../zmk-pmw3610-driver")

# PMW3610 のヘッダーファイルとソースファイルを見つけるためのパス
# ヘッダーはモジュールルート直下、ソースは src/ にあると想定
include_directories(${PMW3610_MODULE_DIR}/src)
include_directories(${PMW3610_MODULE_DIR})

# ソースファイルをアプリケーションのビルドに直接追加
# sayu-hub のリポジトリ構造では src/pmw3610.c にあると推測します
target_sources(app PRIVATE
    ${PMW3610_MODULE_DIR}/src/pmw3610.c
)
