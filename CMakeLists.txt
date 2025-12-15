# zmk-config-moNa2-v2_custom/CMakeLists.txt の内容

# ZMKのカスタムモジュール用としてライブラリを定義
zephyr_library()

# west.yml で定義したモジュール名 'zmk-pmw3610-driver' をパスとして取得
# ${ZEPHYR_BASE}/../{モジュール名} は west build 環境での一般的なパス構造です。
set(PMW3610_MODULE_DIR "${ZEPHYR_BASE}/../zmk-pmw3610-driver")

# PMW3610 ドライバのヘッダーファイルが見つかるようにインクルードパスを追加
# (PMW3610 ドライバのソースが 'drivers/sensor/pmw3610' にあると仮定)
include_directories(${PMW3610_MODULE_DIR}/drivers/sensor/pmw3610)

# PMW3610 のソースファイル (pmw3610.c) をアプリケーションのビルドに直接追加
# これにより、リンカーエラーの原因となっていたシンボルが生成されます。
target_sources(app PRIVATE
    ${PMW3610_MODULE_DIR}/drivers/sensor/pmw3610/pmw3610.c
)
