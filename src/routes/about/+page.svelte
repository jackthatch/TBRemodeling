<script lang='ts'>

    import { Stepper, Step } from '@skeletonlabs/skeleton';

    function onCompleteHandler(e: Event): void {
        window.location.href = '/contact';
    }


</script>

<main>

    <h1 class="p-4 text-center flex justify-center font-bold"> About Us </h1>

    <div class="card p-4 text-center flex justify-center container h-1/2 mx-auto gap-4 flex flex-col py-4">
        <p> Welcome to Top Tier Beast Remodeling Inc., your home remodeling experts located in Decatur, Alabama and serving the surrounding communities. 
            We specialize in roofing, fencing, flooring, and painting, transforming houses into 
            personalized havens. Our team of skilled professionals is dedicated to delivering excellence 
            in every project, making your dream home a reality. From sturdy roofs to elegant fences,
             vibrant walls, and comfortable flooring, we take pride in curating spaces that reflect your 
             unique style and personality. Discover the potential of your home with Top Beast Remodeling 
             Inc. One call is all it takes to turn your vision into a masterpiece. Let's embark on this 
             exciting journey together!
            </p>

            

    </div>

    <div class="card p-4 my-8 text-center flex justify-center container h-1/2 mx-auto gap-4 flex flex-col py-4">

        <Stepper on:complete={onCompleteHandler}>
            <Step>
                <svelte:fragment slot="header">Request a Quote</svelte:fragment>

                <p>
                    Contact by phone at XXX-XXX-XXXX or submit inquiry through the form in the
                    <a href="/contact">{@html 'contact page'}</a>
                    .
                </p>
  
            </Step>
            <Step>
                <svelte:fragment slot="header">Discuss with Our Designer</svelte:fragment>
                <p>
                    After requesting a quote you will receive a call from from one of our professionals to get a better understanding of what you are
                    looking for, as well as provide personalized recommendations.
                </p>
            </Step>

            <Step>
                <svelte:fragment slot="header">Receive a Quote</svelte:fragment>
                <p>
                    After discussing your plans with our team we will visit your home to get measurements and provide a finalized quote.
                    Optionally, for certain projects like fencing, you can submit the dimensions of your yard and skip the in-person visit.
                    (Note: this is a free visit) 
                </p>
            </Step>

            <Step>
                <svelte:fragment slot="header">Watch Your Dream Come to Life</svelte:fragment>
                <p>
                    Finally, our team will begin crafting the dream vision that you have for your home.
                    Current turn-around time is about one week, but outstanding projects and weather can affect this. 
                    Ready to set you dream home in motion this week?
                    <a href="/contact">{@html 'Contact Us Now!'}</a>
                </p>
            </Step>



        </Stepper>

    </div>
    
			

</main>

<style>
    a {
      text-decoration: underline;
      color: #007bff;
    }
  </style>