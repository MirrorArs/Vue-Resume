<template>
    <div id="preview">
        <section class="profiel">
            <h1>{{resume.profile.name || '黄海靖'}}</h1>
            <p class="slogan">{{resume.profile.introduction || '做更好的用户体验'}}</p>
            <p>
                <small>{{resume.profile.job || '目标:前端程序员'}} | {{resume.profile.birth || '19950508'}} | {{resume.profile.city || '潍坊'}}</small>
            </p>
        </section>
        <section class="studyItems">
            <h2>教育经历</h2>
            <ul>
                <li v-for="studyItem in filter(resume.StudyHistory)" v-bind:key="studyItem">
                    {{studyItem.school }} | {{studyItem.profession}} | {{studyItem.education }} | 毕业时间：{{studyItem.graduation | formatDate}}
                </li>
            </ul>
        </section>
        <section class="workItems">
            <h2>工作经历</h2>
            <ul class="items">
                <li v-for="workItem in filter(resume.WorkHistory)" v-bind:key="workItem">
                    <h3>{{workItem.company}}</h3>
                    <p>{{workItem.post }}</p>
                    <p>{{workItem.content}}</p>
                </li>
            </ul>
        </section>
        <section class="projectItems">
            <h2>项目经历</h2>
            <ul>
                <li v-for="projectItem in filter(resume.ProjectsHistory)" v-bind:key="projectItem">
                    <h3>{{projectItem.projectName }}</h3>
                    <p>{{projectItem.responsibilities}}</p>
                    <p>{{projectItem.beginTime | formatDate}}-{{projectItem.endTime | formatDate}}</p>
                    <p>{{projectItem.projectIntroduction}}</p>
                </li>
            </ul>
        </section>
        <section class="honorItems">
            <h2>获奖经历</h2>
            <ul>
                <li v-for="honorItem in filter(resume.HonorsHistory)" v-bind:key="honorItem">
                    <h3>{{honorItem.awards}}</h3>
                    <p>{{honorItem.honorDate | formatDate}}</p>
                </li>
            </ul>
        </section>
        <section class="contact">
            <h2>联系方式</h2>
            <div>
                <p>电话：{{resume.ContactInformation.phone || '18663661644'}}</p>
                <p>邮箱：{{resume.ContactInformation.email || 'sodaone@163.com'}}</p>
                <p>个人主页：{{resume.ContactInformation.blog || 'https://github.com/MirrorArs'}}</p>
            </div>
        </section>
    </div>
</template>

<script>
import {formatDate} from '../comment/date.js';
export default {
    props: ['resume'],
    methods: {
        filter(array) { // 找出非空对象
            return array.filter(item => !this.isEmpty(item))
        },
        isEmpty(object) { // 只要有一个 value 不是 falsy，就返回 flase
            let empty = true
            for (let key in object) {
                if (object[key]) {
                    empty = false
                    break
                }
            }
            return empty
        }
    },
            filters: {
        formatDate(time) {
            let date = new Date(time)
            return formatDate(date, 'yyyy-MM-dd')
        }
    }
}
</script>

<style lang="scss">
#preview {
    box-sizing: border-box;
    font-weight: normal;
    padding: 48px;
    >.profiel {
        padding-bottom: 32px;
        border-bottom: 1px solid #DADADA;
        font-size: 18px;
    }
    >section h2 {
        background: #20A0FF;
        color: #fff;
        padding: 15px;
        width: 115px;
        font-weight: 400;
    }
    >.contact {
        padding: 32px 0; // border: 1px solid red;
        color: #333;
        >div {
            padding-top: 16px;
            >p {
                font-size: 18px;
            }
        }
    }
    >.workItems {
        padding: 32px 0 12px 0;
        border-bottom: 1px solid #DADADA;
        >ul {
            list-style: disc;
            padding: 32px 16px 0px 16px;
            >li {
                padding-bottom: 20px;
                h3 {
                    font-size: 20px;
                    font-weight: normal;
                    padding-bottom: 10px;
                }
                p {
                    font-size: 16px;
                    padding-bottom: 10px;
                    white-space: pre-line;
                }
            }
        }
    }
    >.studyItems {
        padding: 32px 0;
        border-bottom: 1px solid #DADADA;
        >ul li {
            padding: 20px 0 0 0;
            font-size: 16px;
        }
    }

    >.projectItems {
        padding: 32px 0 12px 0;
        border-bottom: 1px solid #DADADA;
        >ul {
            list-style: disc;
            padding: 32px 16px 0px 16px;
            >li {
                padding-bottom: 20px;
                h3 {
                    font-size: 20px;
                    font-weight: normal;
                    padding-bottom: 10px;
                }
                p {
                    font-size: 16px;
                    padding-bottom: 10px;
                    white-space: pre-line;
                }
            }
        }
    }
    >.honorItems {
        padding: 32px 0 12px 0;
        border-bottom: 1px solid #DADADA;
        >ul {
            list-style: disc;
            padding: 32px 16px 0px 16px;
            >li {
                padding-bottom: 20px;
                h3 {
                    font-size: 20px;
                    font-weight: normal;
                    padding-bottom: 10px;
                }
                p {
                    font-size: 16px;
                    padding-bottom: 10px;
                    white-space: pre-line;
                }
            }
        }
    }
}
</style>