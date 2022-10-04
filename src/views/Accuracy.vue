<template>
    <div class="accuracy">
        <b-container>
            <h1 class="text-left mt-3">Accuracy Model</h1>
            <hr />
            <b-row>
                <b-col cols="6">
                    <div class="div-left">
                        <h5>Confusion Matrix</h5>
                        <div class="div-content">
                            <img src="../assets/confusion_matrix.png" width="100%">
                        </div>
                    </div>
                </b-col>
                <b-col cols="6">
                    <div class="div-right-top">
                        <h5>Accuracy Model</h5>
                        <div class="div-content">
                            <div class="mx-auto" style="height: 30px;"></div>
                                <h1 class="h1">82.45%</h1>
                            </div>
                        </div>
                        <div class="div-right-bottom">
                            <h5>Classification Report</h5>
                            <div class="div-content">
                                <img src="../assets/classification_report.png" width="80%">
                            </div>
                        </div>
                </b-col>
            </b-row>
        </b-container>
    </div>
</template>
<style>
.div-left {
    background-color: #D8F2FF !important;
    padding-top: 10px;
    height: 450px;
    background: #3d3d3d;
    box-shadow: 0 4px 8px 0 rgba(187, 187, 187, 0.2), 0 6px 20px 0 rgba(209, 209, 209, 0.19);
    border-radius: 20px;
}

.div-right-top {
    background-color: #D8F2FF !important;
    padding-top: 10px;
    height: 140px;
    background: #3d3d3d;
    box-shadow: 0 4px 8px 0 rgba(187, 187, 187, 0.2), 0 6px 20px 0 rgba(209, 209, 209, 0.19);
    border-radius: 20px;
}

.div-right-bottom {
    background-color: #D8F2FF !important;
    padding-top: 10px;
    height: 195px;
    margin-top: 60px;
    background: #3d3d3d;
    box-shadow: 0 4px 8px 0 rgba(187, 187, 187, 0.2), 0 6px 20px 0 rgba(209, 209, 209, 0.19);
    border-radius: 20px;
}

.div-content {
    background-color: white !important;
    border-radius: 20px;
    padding: 10px;
    box-shadow: 0 4px 8px 0 rgba(187, 187, 187, 0.2), 0 6px 20px 0 rgba(209, 209, 209, 0.19);
    height: 100%;
}

.accuracy {
    /* background-color: #F6FCFF !important; */
    margin-top: -16px;
    padding-top: 16px;
}

h5 {
    text-align: center;
    color: #03A9F4;
}

.h1 {
    text-align: center;
    color: #03A9F4;
}
</style>