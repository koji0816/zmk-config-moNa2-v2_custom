# zmk-config-moNa2-v2_custom/CMakeLists.txt の修正後の内容

zephyr_library()

set(PMW3610_MODULE_DIR "${ZEPHYR_BASE}/../zmk-pmw3610-driver")

# 修正1: ヘッダーファイルのパスを調整 (モジュールのルート直下を想定)
# ZMKモジュールはインクルードパスにルートを追加している可能性が高い
# 以下の行は不要な可能性があるが、念のため残しておく
# include_directories(${PMW3610_MODULE_DIR})

# 修正2: ソースファイルのパスを調整
# 多くのZMK外部モジュールは 'src/' ディレクトリにソースを配置します。
target_sources(app PRIVATE
    ${PMW3610_MODULE_DIR}/src/pmw3610.c
)
