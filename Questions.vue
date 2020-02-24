<template>
    <div>
        <div class="columns main">
            <div class="column is-1 numbers">
                <div v-for="qnum in qs" :key="qnum.id" @click="activeQ = qnum.id">
                    {{ qnum.id }}
                </div>
            </div>
            <div class="column is-4">
                <div v-if="activeQ === 1">
                    {{ Q1 }}
                </div>
                <div v-else-if="activeQ === 2">
                    {{ Q2 }}
                </div>
                <div v-else-if="activeQ === 3">
                    {{ Q3 }}
                </div>
                <div v-else-if="activeQ === 4">
                    {{ Q4 }}
                </div>
                <div v-else-if="activeQ === 5">
                    {{ Q5 }}
                </div>
            </div>
            <div class="column is-7">
                <div class="editOption">
                    <div>Write Your Code Below</div>
                    <div><select name="type" v-modal="selected">
                        <option value="light">Light</option>
                        <option value="monokai">MOnokai</option>
                        <option value="dark">Dark</option>
                    </select>
                </div>
                <div v-if="selected === 'light'">
                    <codemirror v-modal="code" :options="cmlight"></codemirror>
                </div>
                <div v-if="selected === 'monokai'">
                    <codemirror v-modal="code" :options="cmmonokai"></codemirror>
                </div>
                <div v-if="selected === 'dark'">
                    <codemirror v-modal="code" :options="dark"></codemirror>
                </div>
            </div>
        </div>
        </div>
    </div>
</template>

<style scoped>
    .numbers {
        display: flex;
        flex-direction: column;
        justify-content: flex-start;
    }

    .editOption {
        display: flex;
        flex-direction: row;
        justify-content: space-between;
    }

    .main {
        background: rgb(65, 62, 62);
        height: 100%;
        padding: 10px 10px 10px 10px;
    }
</style>

<script>
import  codemirror from 'codemirror/mode/clike/clike.js'
import 'codemirror/theme/base16-dark.css'

import firebaseApp from '../firebaseConfig'

export default {
    name: 'Questions',
    components: {
        codemirror,
    },
    data: function() {
        return {
            qs: [
                {
                    id: 1
                },
                {
                    id: 2
                },
                {
                    id: 3
                },
                {
                    id: 4
                },
                {
                    id: 5
                }
            ],
            activeQ: 0,
            Q1: 'Question 1:Given a string and that 0 = Gryffindor , 1 = Slytherin , 2 = Hufflepuff and 3 =Ravenclaw, find the sum of the  ascii values of the string and print the name corresponding to that sum modulo 4 (The input is always a single word)For Example : Ron  --> (82 + 111 + 110) = 303  and 303%4 == 3 -> Ravenclaw , therefore the output will be Ravenclaw',
            Q2: 'Question 2:Given a string , replace all the characters in prime positions by _ and print the result. For Example : CodeGolf --> C__e_o_f',
            Q3: 'Question 3:Find the digital root of the number , where the digital root is the single digit sum of all the digits in the number and print the result.For Example : 1238 -> 1+2+3+8 = 14 -> 1+4 =5 ;  Therefore digital root of 1238 is 5',
            Q4: 'Question 4:Given a integer input n, print a pyramid pattern (Note the inputs are always odd numbers)',
            Q5: 'Question 5:Sort an array in the ascending order. The input is in the format of an integer n and a set of n space separted inputs in the next line.For Example:input : 5 4 7 1 0 3 output : 0 1 3 4 7',
            selected: '',
            cmlight: {
                tabSize: 4,
                mode: 'text/clike',
                theme: 'base16-dark',
                lineNumbers: true,
                line: true
            },
            cmmonokai: {
                tabSize: 4,
                mode: 'text/clike',
                theme: 'base16-dark',
                lineNumbers: true,
                line: true
            },
            cmdark: {
                tabSize: 4,
                mode: 'text/clike',
                theme: 'base16-dark',
                lineNumbers: true,
                line: true
            }
        }
    }
}
</script>