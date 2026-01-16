<template>
    <div class="container-fluid fixed-top custom-header">
        <div class="row">
            <div class="col-4">
                HEADER
            </div>
            <div class="col-4">

            </div>
            <div class="col-4">

            </div>
        </div>
        <div class="row">
            <div class="col">
                HEADER 1
            </div>
        </div>
        <div class="row">
            <div class="col">
                <el-tabs v-model="activePhase" type="card" class="phase-tabs">
                    <el-tab-pane label="DEFINE" name="define">
                        <el-tabs v-model="activeDefineTab" class="define-tabs">
                            <el-tab-pane label="Empathy Map" name="empathy-map">
                                <p class="tab-description">
                                    Empathy map dédiée pour cadrer les besoins utilisateurs.
                                </p>
                            </el-tab-pane>
                            <el-tab-pane v-if="!isPresentationMode" label="Outils" name="tools">
                                <p class="tab-description">
                                    Liste des outils utiles à la phase DEFINE.
                                </p>
                            </el-tab-pane>
                        </el-tabs>
                    </el-tab-pane>
                </el-tabs>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: "Header",
        data() {
            return {
                activePhase: "define",
                activeDefineTab: "empathy-map",
            }
        },
        computed: {
            isPresentationMode() {
                return new URLSearchParams(window.location.search).get("presentation") === "true";
            }
        }
    }
</script>

<style scoped lang="scss">
    .custom-header {
        background-color: $main-color;
        height: $header-height + $header1-height;
    }

    .phase-tabs {
        background-color: transparent;
    }

    .define-tabs {
        margin-top: 8px;
    }

    .tab-description {
        margin: 0;
    }
</style>
