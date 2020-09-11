<template>
  <div class="container">
    <form action="">
      <div class="inner-container bg-light">
        <h3>Program Design</h3>
        <div class="design bg-white">
          <div class="d-flex justify-content-around program-title">
            <div class="flex-fill">
              <label for="title">What's the title of your program?</label>
              <b-form-input v-model="name" placeholder="Please enter the title of your program"></b-form-input>
            </div>
            <div>
              <label for="start">Start Date</label>
              <b-form-input v-model="start_date" placeholder="E.g. 01/01/2020"></b-form-input>
            </div>
            <div>
              <label for="end">End Date</label>
              <b-form-input v-model="end_date" placeholder="E.g. 01/01/2020"></b-form-input>
            </div>
          </div>
          <div>
            <label for="issues">What issues are you trying to solve in this program?</label>
            <b-tags v-model="problem" no-outer-focus >
      <template v-slot="{ tags, inputAttrs, inputHandlers, tagVariant, removeTag }">
        <b-input-group class="mb-2">
          <b-form-input
            v-bind="inputAttrs"
            v-on="inputHandlers"
            placeholder="Write problems and press enter"
          ></b-form-input>
        </b-input-group>
        <div class="d-inline-block" style="font-size: 1.5rem;">
          <b-form-tag
            v-for="tag in tags"
            @remove="removeTag(tag)"
            :key="tag"
            :title="tag"
            :variant="tagVariant"
            class="mr-1"
          >{{ tag }}</b-form-tag>
        </div>
      </template>
    </b-tags>
          </div>
          <div>
            <label for="goals">What are your goals for this program?</label>
             <b-tags v-model="goal_objective" no-outer-focus >
      <template v-slot="{ tags, inputAttrs, inputHandlers, tagVariant, removeTag }">
        <b-input-group class="mb-2">
          <b-form-input
            v-bind="inputAttrs"
            v-on="inputHandlers"
            placeholder="Write problems and press enter"
          ></b-form-input>
        </b-input-group>
        <div class="d-inline-block" style="font-size: 1.5rem;">
          <b-form-tag
            v-for="tag in tags"
            @remove="removeTag(tag)"
            :key="tag"
            :title="tag"
            :variant="tagVariant"
            class="mr-1"
          >{{ tag }}</b-form-tag>
        </div>
      </template>
    </b-tags>
          </div>
        </div>
        <h3>Outcome Measurement Framework</h3>
        <div class="design bg-white">
          <div>
            <h4 class="text-primary">Inputs</h4>
            <p class="font-weight-bold">What Resources are available for this program?</p>
          </div>
          <div>
            <label for="personnel">Which personnel will be in this program?</label>
            <b-tags v-model="personnel" no-outer-focus >
      <template v-slot="{ tags, inputAttrs, inputHandlers, tagVariant, removeTag }">
        <b-input-group class="mb-2">
          <b-form-input
            v-bind="inputAttrs"
            v-on="inputHandlers"
            placeholder="Select personnel"
          ></b-form-input>
        </b-input-group>
        <div class="d-inline-block" style="font-size: 1.5rem;">
          <b-form-tag
            v-for="tag in tags"
            @remove="removeTag(tag)"
            :key="tag"
            :title="tag"
            :variant="tagVariant"
            class="mr-1"
          >{{ tag }}</b-form-tag>
        </div>
      </template>
    </b-tags>
          </div>
          <div>
            <label for="funding">Add funding source</label>
             <b-tags v-model="program_fundings" no-outer-focus >
      <template v-slot="{ tags, inputAttrs, inputHandlers, tagVariant, removeTag }">
        <b-input-group class="mb-2">
          <b-form-input
            v-bind="inputAttrs"
            v-on="inputHandlers"
            placeholder="Select and press enter"
          ></b-form-input>
        </b-input-group>
        <div class="d-inline-block" style="font-size: 1.5rem;">
          <b-form-tag
            v-for="tag in tags"
            @remove="removeTag(tag)"
            :key="tag"
            :title="tag"
            :variant="tagVariant"
            class="mr-1"
          >{{ tag }}</b-form-tag>
        </div>
      </template>
    </b-tags>
          </div>
          <div>
            <label for="partners">Who are also partnering with you in this program?</label>
             <b-tags v-model="program_partners[0].program_partner_orgs" no-outer-focus >
      <template v-slot="{ tags, inputAttrs, inputHandlers, tagVariant, removeTag }">
        <b-input-group class="mb-2">
          <b-form-input
            v-bind="inputAttrs"
            v-on="inputHandlers"
            placeholder="Select partner organizations"
          ></b-form-input>
        </b-input-group>
        <div class="d-inline-block" style="font-size: 1.5rem;">
          <b-form-tag
            v-for="tag in tags"
            @remove="removeTag(tag)"
            :key="tag"
            :title="tag"
            :variant="tagVariant"
            class="mr-1"
          >{{ tag }}</b-form-tag>
        </div>
      </template>
    </b-tags>
          </div>
          <div>
            <label for="resources">What other resources you have?</label>
             <b-tags v-model="program_others[0].program_others_list" no-outer-focus >
      <template v-slot="{ tags, inputAttrs, inputHandlers, tagVariant, removeTag }">
        <b-input-group class="mb-2">
          <b-form-input
            v-bind="inputAttrs"
            v-on="inputHandlers"
            placeholder="Write and press enter"
          ></b-form-input>
        </b-input-group>
        <div class="d-inline-block" style="font-size: 1.5rem;">
          <b-form-tag
            v-for="tag in tags"
            @remove="removeTag(tag)"
            :key="tag"
            :title="tag"
            :variant="tagVariant"
            class="mr-1"
          >{{ tag }}</b-form-tag>
        </div>
      </template>
    </b-tags>
          </div>
        </div>

        <div class="design bg-white">
          <div>
            <h4 class="text-primary">Activities</h4>
            <p class="font-weight-bold">What activities are you planning to do in this program?</p>
          </div>
          <div class="d-flex justify-content-between">
              <b-form-checkbox id="checkbox-1" v-model="status" name="checkbox-1" value="accepted" unchecked-value="not_accepted">
              Sample service
            </b-form-checkbox>
            <b-form-checkbox id="checkbox-1" v-model="status" name="checkbox-1" value="accepted" unchecked-value="not_accepted">
              Sample service
            </b-form-checkbox>
            <b-form-checkbox id="checkbox-1" v-model="status" name="checkbox-1" value="accepted" unchecked-value="not_accepted">
              Sample service
            </b-form-checkbox>
            <b-form-checkbox id="checkbox-1" v-model="status" name="checkbox-1" value="accepted" unchecked-value="not_accepted">
              Sample service
            </b-form-checkbox>
            <b-form-checkbox id="checkbox-1" v-model="status" name="checkbox-1" value="accepted" unchecked-value="not_accepted">
              Sample service
            </b-form-checkbox>
            <b-form-checkbox id="checkbox-1" v-model="status" name="checkbox-1" value="accepted" unchecked-value="not_accepted">
              Sample service
            </b-form-checkbox>
          </div>
        </div>
        <div class="design bg-white">
          <div>
            <h4 class="text-primary">Output</h4>
            <p class="font-weight-bold">What activities are you required to accomplish in this program?</p>
          </div>
          <div>
            <label for="resources">Select your parameters (Number of X)</label>
            <!-- <b-form-input v-model="resources" placeholder="Write and press enter or select from the suggestions"></b-form-input> -->
            <div>
            <label for="funding">Add funding source</label>
             <b-tags v-model="logic_model.outputs" no-outer-focus >
      <template v-slot="{ tags, inputAttrs, inputHandlers, tagVariant, removeTag }">
        <b-input-group class="mb-2">
          <b-form-input
            v-bind="inputAttrs"
            v-on="inputHandlers"
            placeholder="Write and press enter or select from the suggestions"
          ></b-form-input>
          <b-input-group-append>
            <b-button @click="addTag()" variant="primary">Add</b-button>
          </b-input-group-append>
        </b-input-group>
        <div class="d-inline-block" style="font-size: 1.5rem;">
          <b-form-tag
            v-for="tag in tags"
            @remove="removeTag(tag)"
            :key="tag"
            :title="tag"
            :variant="tagVariant"
            class="mr-1"
          >{{ tag }}
          <b-form-input v-model="text" placeholder="0"></b-form-input>
          </b-form-tag>
        </div>
      </template>
    </b-tags>
          </div>
          </div>
        </div>
        <div class="design bg-white">
          <div>
            <h4 class="text-primary">Measure of Achievement</h4>
            <p class="font-weight-bold">How would you define your success?</p>
          </div>
          <div v-for="output in logic_model.outputs" :key="output" class="flex">
            <div class="mr-1 mb-1">{{output}}</div>
            <b-form-select v-model="selected" :options="options" class="mr-1 mb-1"></b-form-select>
            <b-form-input v-model="text" placeholder="Enter your name"></b-form-input>
          </div>
        </div>
        <div class="design bg-white">
          <div>
            <h4 class="text-primary">Outcome</h4>
            <p class="font-weight-bold">What are the intended outcomes of your program?</p>
            <div v-for="(goal,index) in goal_objective" :key="goal">
              <p class="text-danger font-weight-bold">Goal {{index+1}} : goal</p>
              <label for="funding">Select your outcome parameters</label>
             <b-tags v-model="logic_model.outcome" no-outer-focus >
      <template v-slot="{ tags, inputAttrs, inputHandlers, tagVariant, removeTag }">
        <b-input-group class="mb-2">
          <b-form-input
            v-bind="inputAttrs"
            v-on="inputHandlers"
            placeholder="Write and press enter or select from the suggestions"
          ></b-form-input>
        </b-input-group>
        <div class="d-inline-block" style="font-size: 1.5rem;">
          <b-form-tag
            v-for="tag in tags"
            @remove="removeTag(tag)"
            :key="tag"
            :title="tag"
            :variant="tagVariant"
            class="mr-1"
          >{{ tag }}</b-form-tag>
        </div>
      </template>
    </b-tags>
            </div>
          </div>
        </div>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: 'Home',
  data () {
    return {
      selected: null,
      options: [
        { value: null, text: 'Please select an option' },
        { value: 'Number', text: 'Number' },
        { value: 'Percentage', text: 'Percentage' }
      ],
      status: 'not_accepted',
      logic_model: {
        id: '',
        inputs: [],
        activities: [],
        outputs: [],
        achievements: [],
        outcome: [],
        org: 2,
        program: ''
      },
      problem: [{
        id: 85,
        name: 'problem 1'
      }, {
        id: 85,
        name: 'problem 2'
      }],
      goal_objective: [],
      services: [{
        id: 5,
        title: 'Sample 2',
        is_checked: true
      }, {
        id: 5,
        title: 'Sample 3',
        is_checked: true
      }],
      personnel: [{
        name: 'Asad',
        individual: 34
      }, {
        name: 'Rahim',
        individual: 34
      }, {
        name: 'Karim',
        individual: 34
      }],
      program_accomplishments: [{
        id: 18,
        program_accomplishment_list: [{
          accomplishment_id: 3,
          title: 'Number of paid participants on field trips'
        }]
      }],
      program_fundings: [{
        id: 15,
        program_fundings_list: [{
          id: 3,
          first_name: 'Trump Foundation'
        }]
      }],
      program_partners: [{
        id: 17,
        program_partner_orgs: [{
          id: 2,
          name: 'Boeing'
        }],
        program: 104
      }],
      program_others: [{
        id: 18,
        program_others_list: [{
          name: 'daf'
        }],
        program: 104
      }],
      name: '',
      mission: '',
      type: 1,
      start_date: '2000-09-09',
      end_date: '2008-09-09',
      org: 2

    }
  },
  methods: {
  }
}
</script>

<style>
.program-title div{
  padding-right: 10px;
}
.design > div{
  padding: 10px;
}
.inner-container{
  padding:30px;
}
.inner-container > div{
  margin-top: 20px;
}
hr{
  border-style:dashed;
}
.design{
  padding:10px;
}
.b-form-tags{
  border:none;
}

</style>
