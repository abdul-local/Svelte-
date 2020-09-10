
  
<script>
  import Modal from './Modal.svelte';
  

     export let charities;
     
     function calculateFunded(pladge,target){
       return Math.round( (1/(target/pladge)) *100);
     }
     function formatCurrency(nominal){
       return nominal.toLocaleString('id-ID',{
         style: 'currency',
         currency: 'IDR',
       });
     }
     function remainCalculate(date_end){
       const delta = date_end -new Date();
       const oneday = 24 *60*60*1000;
       return Math.round(Math.abs(delta/oneday));
     }
    
</script>
<style>
  .xs-list-with-content{
    font-size: 12px;
  }
  .show{
    display: block;
    background-color: rgb(0,0,0,0.45);
  }
</style>

  
  <!-- popularCauses section -->
  <section id="popularcause" class="bg-gray waypoint-tigger xs-section-padding">
    <div class="container">
      <div class="xs-heading row xs-mb-60">
        <div class="col-md-9 col-xl-9">
          <h2 class="xs-title">Popular Causes</h2>
          <span class="xs-separetor dashed"></span>
          <p>FundPress has built a platform focused on aiding entrepreneurs, startups, and <br> companies
            raise capital from anyone.</p>
        </div><!-- .xs-heading-title END -->
      </div><!-- .row end -->
      
      {#each charities as charity}
      <div class="row">
        <div class="col-lg-4 col-md-6">
          <!-- modal goes here -->
          <!-- Modal -->
          <div class="xs-popular-item xs-box-shadow">
            <div class="xs-item-header">

              <img src="{charity.thumbnail}" alt="">

              <div class="xs-skill-bar">
                <div class="xs-skill-track">
                  <p><span class="number-percentage-count number-percentage" data-value="90"
                      data-animation-duration="3500">{calculateFunded(charity.pladge, charity.target)}</span>%</p>
                </div>
              </div>
            </div><!-- .xs-item-header END -->
            <div class="xs-item-content">
              <ul class="xs-simple-tag xs-mb-20">
                <li><a href="">{charity.category}</a></li>
              </ul>

              <a href="#" class="xs-post-title xs-mb-30">{charity.title}</a>

              <ul class="xs-list-with-content">
                <li>{formatCurrency(charity.pladged)}<span>pladge</span></li>
                <li><span class="number-percentage-count number-percentage" data-value="90"
                    data-animation-duration="3500">{calculateFunded(charity.pladged, charity.target)}</span>% <span>Funded</span></li>
                <li>{remainCalculate(charity.date_end)}<span>Days to go</span></li>
              </ul>

              <span class="xs-separetor"></span>

              <div class="row xs-margin-0">
                <div class="xs-round-avatar">
                  <img src="{charity.profile_photo}" alt="">
                </div>
                <div class="xs-avatar-title">
                  <a href="#"><span>By</span>{charity.profile_name}</a>
                </div>
              </div>

              <span class="xs-separetor"></span>

              <a href="/donation/{charity.id}" data-toggle="modal" data-target="#exampleModal"
                class="btn btn-primary btn-block">
                Donate This Cause
              </a>
            </div><!-- .xs-item-content END -->
          </div><!-- .xs-popular-item END -->
        </div>
      </div><!-- .row end -->
      {/each}
      
    </div><!-- .container end -->
  </section><!-- End popularCauses section -->
