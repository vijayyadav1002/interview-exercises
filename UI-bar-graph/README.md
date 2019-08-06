# UI-bar-graph exercise

## Instructions

- Using any UI framework (or none) create a bar graph using the data.json file provided using javascript and css
- Do not use any third party graph libraries, the graph should be your own
- After you complete the exercise, provide notes below on how your code can be ran whether it be by simply opening a index.html file or through an npm command

## Candidate Notes:

//bar-chart.component.html

<div class="chart-container">
    <div class="stack-chart">
        <div class="stack-bar">
            <div class="top-bar" [style.height] = "topBarHeight">

            </div>
            <div class="bottom-bar" [style.height] = "bottomBarHeight">
                
            </div>
        </div>
    </div>
</div>

<---------------------------------------------------------------------->

//bar-chart.component.ts

import { Component, Input, OnInit } from '@angular/core';

 
@Component({

  selector: 'stack-chart',

  templateUrl: './stack-chart.component.html',

  styleUrls: ['./stack-chart.component.less']

})

export class StackChartComponent {

 

  private _topBar: number;

  @Input() set topBar(value: number) {

    this._topBar = value || null;

  }

  get topBar() {

    return this._topBar;

  }

 

  private _bottomBar: number;

  @Input() set bottomBar(value: number) {

    this._bottomBar = value || null;

  }

  get bottomBar() {

    return this._bottomBar;

  }

 

  get topBarHeight() {

    if (this.topBar == null) {

      return '0%';

    }

    else {

      return Math.ceil((this.topBar / (this.topBar + this.bottomBar)) * 100) + '%';

    }

  }

 

  get bottomBarHeight() {

    if (this.bottomBar == null) {

      return '0%';

    }

    else {

      return Math.ceil((this.bottomBar / (this.topBar + this.bottomBar)) * 100) + '%';

    }

 

  }

}


<-------------------------------------------------------------->

bar-chart.module.ts

import { NgModule } from '@angular/core'

import { StackChartComponent } from './stack-chart.component'

 

@NgModule({

    declarations: [

      StackChartComponent

    ],

    imports: [],

    exports: [StackChartComponent]

})

 

export class StackChartModule { }


<------------------------------------------------------------->

stack-chart.component.less

.stack-chart {

    width: 100%;

    height: 100%;

    > .stack-Bar {

        position: relative;

        background-color: grey;

        height: 50%;

        margin: 0 5px;

        .top-Bar {

            background-color: green;

            height: 100%;

            margin: 0 5px;

            position: absolute;

            width: 25px;

            bottom: 0;

            max-height: 100%;

        }

        .full-Bar {

            background-color: gray;

            height: 100%;

        }

        .bottom-Bar {

            background-color: blue

            height: 100%;

            margin: 0 5px;

            position: absolute;

            width: 25px;

            top: 0;

            max-height: 100%;

        }

    }

}

 

.chart-container {

    width: 45px;

    height: 121px;

}

